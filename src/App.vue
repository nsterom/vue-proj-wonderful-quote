<template>
    <div class="container">
        <app-header v-bind:quoteCount="quoteList.length" v-bind:maxQuotes="maxQuotes"></app-header>
        <app-new-quote v-on:quoteAdded="newQuote($event)"></app-new-quote>
        <app-quote-grid v-bind:quotes="quoteList" v-on:quoteDeleted="deleteQuote($event)"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete if!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue'
    import NewQuote from './components/NewQuote.vue'
    import Header from './components/Header.vue'

    export default {
        data: function() {
            return {
                quoteList: [
                    'hello world!'
                ],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote: function(quote) {
                if (this.quoteList.length >= this.maxQuotes) {
                    alert('Please remove quote first!')
                }
                this.quoteList.push(quote)
            },
            deleteQuote: function(index) {
                console.log(index)
                this.quoteList.splice(index, 1)
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
