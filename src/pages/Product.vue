<template>
    <div class="wrapper-content wrapper-content--fixed">
        <section>
            <div class="container">
                <div class="product__wrapper">
                    <!--slider-->
                    <div class="product-slider">

<!--                        <img :src="product.img" :alt="product.title">-->

                        <carousel
                            :per-page="1"
                            :pagination-enabled="true"
                            pagination-color="#b3b3b3"
                            pagination-active-color="#494ce8"
                        >
                            <slide v-for="(slide, index) in product.gallery" :key="index">
                                <img :src="slide.img" :alt="slide.name">
                            </slide>
                        </carousel>

                    </div>

                    <!--content-->
                    <div class="product-content">
                        <h1 class="title">{{ product.title }}</h1>
                        <p>{{ product.descr }}</p>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                product: null
            }
        },
        created() {
            //console.log(this.$route);
            let id = this.$route.params.id
            this.product = this.$store.getters.getProduct(id)
            // console.log(product);
        }
    }
</script>

<style lang="scss">
    .product__wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .product-slider,
    .product-content {
        max-width: 48%;
        text-align: center;
    }

    .VueCarousel-inner {
        visibility: visible!important;
        flex-basis: 100%!important;
        width: 100%!important;
    }

</style>