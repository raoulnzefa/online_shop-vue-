<template>
    <div class="v-catalog-item">
        <img class="v-catalog-item_image" :src=" require('../assets/images/' + product_data.image) " alt="img">  
        <p class="v-catalog-item_name">{{product_data.name}}</p>
        <p class="v-catalog-item_price">Price: {{product_data.price}} $.</p>
        <button 
            class="v-catalog-item_add_to_cart_btn btn" 
            @click="addToCart"
        >Add to cart</button>
    </div>
</template>

<script>
export default {
    name: "v-catalog-item",
    props: {
        product_data: {
            type: Object,
            default(){
                return{}
            }
        }
    },
    data(){
        return {}
    },
    computed: {},
    methods: {
        addToCart(){
            this.$emit('addToCart', this.product_data);
        }
        // sendDataToParent(){
        //     this.$emit('sendArticle', this.product_data.article)
        //     // this.$emit( event: 'sendArticle', this.product_data.article)
           
        // }
    },
    mounted() {
        this.$set(this.product_data, 'quantity', 1)
    },
}
</script>

<style lang="scss">

    .v-catalog-item{
        flex-basis: 25%;
        box-shadow: 0 0 8px 0 #e8e8e8;
        padding: $padding*2;
        margin-bottom: $margin*2;
        &_image{
            width: 100px;
        }
    }

</style>