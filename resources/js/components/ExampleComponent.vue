<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Components</div>

                    <div class="card-body" v-for="m in messages">
                        {{ m.data }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                messages: []
            }
        },

        mounted() {


            window.Echo.channel('test-event')
            .listen('ExampleEvent', (e) => {

                this.messages.push(e);
            });

        }
    }
</script>
