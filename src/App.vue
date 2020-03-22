<template>
<html>
<head>
  <link rel="stylesheet" src="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" />
</head>

<body>
  <nav class="navbar navbar-expand-lg navbar-default raja-nav">
    <a class="navbar-brand" href="#">Onlineshopku</a>
    <button class="navbar-toggler custom-toggler float-xs-left" type="button" data-toggle="collapse" data-target="#menu-raja" aria-controls="menu-raja" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
      </button>

  <div class="collapse navbar-collapse" id="menu-raja">
    <ul class="navbar-nav mr-auto mt-2 mt-lg-0 kiri">
      <li class="nav-item active">
        <a class="nav-link" href="#">Home</a>
      </li>
      <li class="nav-item active">
        <a class="nav-link" href="#">Shop</a>
      </li>
      <li class="nav-item active">
        <a class="nav-link" href="#">Features</a>
      </li>
      <li class="nav-item active">
        <a class="nav-link" href="#">Pages</a>
      </li>
      <li class="nav-item active">
        <a class="nav-link" href="#">Blog</a>
      </li>
    </ul>
    <ul class="navbar-nav my-2 my-lg-0 kanan">
      <li class="nav-item">
        <a class="nav-link" href="#">My Account</a>
      </li>
    </ul>
  </div>
</nav>
<div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
  <ol class="carousel-indicators">
    <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
    <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
    <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
  </ol>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img class="d-block w-100 img-carousel" src="./pictures/carousel-1.jpg" alt="First slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100 img-carousel" src="./pictures/carousel-1.jpg" alt="First slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100 img-carousel" src="./pictures/carousel-1.jpg" alt="First slide">
    </div>
  </div>
  <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
<div id="section-kategori">
      <section id="tabs" class="project-tab">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-md-12">
                    <b-tabs content-class="mt-3" fill>
                    <b-tab title="Rekomendasi" active>
                    <ul class="container mt-4">
                          <div class="row">
                            <div v-for="(produk, index) in celana" :key="index" class="col-md-3 mt-5 mb-2 text-center">
                              <div class="card kotak-produk">
                                <img src="./pictures/produk/celana/1.png" class="card-img-top gambar-info" style="background-color:#F0F1F3;">
                              </div>
                              <div class="product-details">
                                <h6 class="display-6 mt-3">{{ produk.name }}</h6>
                                <h6 class="display-6 text-muted">Rp.{{ produk.price }}</h6>
                              </div>
                            </div>
                          </div>
                    </ul>
                    </b-tab>
                    <b-tab title="Terlaris">
                      <ul class="container mt-4">
                        <div class="row">
                            <div v-for="(produk, index) in celana" :key="index" class="col-md-3 mt-5 mb-2 text-center">
                              <div class="card kotak-produk">
                                <img v-bind:src="'/pictures/produk/celana/' + produk.pictures" class="card-img-top gambar-info">
                              </div>
                              <div class="product-details">
                                <h6 class="display-6 mt-3">{{ produk.name }}</h6>
                                <h6 class="display-6 text-muted">Rp.{{ produk.price }}</h6>
                              </div>
                            </div>
                          </div>
                      </ul>
                      </b-tab>
                    <b-tab title="Terbaru">
                      <ul class="container mt-4">
                        <div class="row">
                            <div v-for="(produk, index) in celana" :key="index" class="col-md-3 mt-5 mb-2 text-center">
                              <div class="card kotak-produk">
                                <img v-bind:src="'/pictures/produk/celana/' + produk.pictures" class="card-img-top gambar-info">
                              </div>
                              <div class="product-details">
                                <h6 class="display-6 mt-3">{{ produk.name }}</h6>
                                <h6 class="display-6 text-muted">Rp.{{ produk.price }}</h6>
                              </div>
                            </div>
                          </div>
                      </ul>
                    </b-tab>
                  </b-tabs>

                    </div>
                </div>
            </div>
            </section>
        </div>
</body>
</html>
</template>

<script>
import axios from 'axios'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
// import data from '../db.json'

export default {
  name: 'App',
  data () {
    return {
      baju: [],
      sepatu: [],
      celana: []
    }
  },
  async created () {
    axios.get('http://localhost:8080/db.json')
      .then((result) => {
        this.baju = result.data.baju
        this.sepatu = result.data.sepatu
        this.celana = result.data.celana
      })
  }
}

</script>

<style>
@media (min-width: 992px) {
      .navbar-brand {
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        font-family: "Poppins",sans-serif;
        color: #23232c;
        letter-spacing: 2.5px;
      }
    }
    .kiri {
      margin-left: 40px;
    }
    .kanan {
      margin-right: 40px;
    }
    @media (max-width: 991px) {
      .navbar-brand {
        height: 0;
        left: 10%;
      }
      .navbar-nav{
        margin-top: 10px;
        margin-left: 40%;
      }
    }
    .raja-nav{
      padding-top: 25px;
      padding-bottom: 25px;
      font-family: Laila, serif;
      font-size: 1.2rem;
      color: #23232c;
      font-weight: 600;
      text-transform: uppercase;
    }
    .navbar-nav > li > a:hover {
      /*  */
    }
    .navbar-toggler-icon {
      background-image: url("data:image/svg+xml;charset=utf8,%3Csvg viewBox='0 0 32 32' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath stroke='rgba(34, 155, 168, 1)' stroke-width='2' stroke-linecap='round' stroke-miterlimit='10' d='M4 8h24M4 16h24M4 24h24'/%3E%3C/svg%3E");
    }
    .navbar-nav > li{
      margin-right: 20px;
    }
    .navbar-nav > li > a{
      color: #23232c;
      font-size: 14px;
      font-family: "Poppins",sans-serif;
    }
    .navbar-toggler {
      margin-left: 90%;
    }
    .carousel-item {
      height: 100vh;
      min-height: 350px;
      background: no-repeat center center scroll;
      -webkit-background-size: cover;
      -moz-background-size: cover;
      -o-background-size: cover;
      background-size: cover;
    }
    .img-carousel {
      object-fit: cover;
      height: 100%;
    }

#my-jumbotron {
    background-size: cover;
    overflow: hidden;
}
#jumbo-text-contain {
    color: black;
    min-height: 400px;
}
#jumbotron-btn {
    font-size: 20px;
    border: 3px solid ;
    border-radius: 0;
    transition: 0.3s;
}
#jumbotron-btn:hover {
    color:white ;
    border: 1px solid white;
}
#products-container li{
    list-style-type: none;
    height: 250px;
}
.product-image {
    background: #f4f4ef;
    width: 250px;
    height: 275px;
}
.project-tab {
    padding-top : 10%;
    padding-bottom : 10%;
    margin-top: -8%;
}
.project-tab #tabs{
    background: #007b5e;
    color: #eee;
}
.project-tab #tabs h6.section-title{
    color: #eee;
}
.project-tab #tabs .nav-tabs .nav-item.show .nav-link, .nav-tabs .nav-link.active {
    color: #20232a;
    background-color: transparent;
    border-color: transparent transparent #f3f3f3;
    border-bottom: 3px solid !important;
    font-size: 16px;
    font-weight: bold;
}
.project-tab .nav-link {
    border: 1px solid transparent;
    border-top-left-radius: .25rem;
    border-top-right-radius: .25rem;
    color: #acbebe;
    font-size: 16px;
    font-weight: 600;
}
.project-tab .nav-link:hover {
    border: none;
}
.project-tab thead{
    background: #f3f3f3;
    color: #333;
}
.project-tab a{
    text-decoration: none;
    color: #333;
    font-weight: 600;
}
.kotak-produk {
  border-width: 25px;
  border-color: #F0F1F3;
}

.nav-tabs {
  border-bottom: none !important;
}

#section-kategori {
  margin-top: 40px;
}
</style>
