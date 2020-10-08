<template>
    <div class="container mt-5">
        <form @submit.prevent="addTodo()" class="custom">            
            <div class="d-flex">
                <input v-model="newTodo" type="text" class="form-control mr-1">
                <button type="submit" class="btn btn-primary">submit</button>
            </div>
            <div v-for="(todo, index) in todos" :key="index">
                <div class="d-flex justify-content-between">
                    <input class="mt-1" type="checkbox" v-model="todo.done">
                    <span :class="{done: todo.done}">{{todo.title}}</span>
                    <span><i class="fa fa-trash" @click="deleteTodo(todo)"></i></span>
                </div>
            </div>            
        </form>
    </div>
</template>
<script>
export default {
    data() {
        return {
            newTodo: "",
            todos: [
                {title: 'Vue JS', done: false}
            ]
        }
    },
    methods:{
        addTodo(){
            if (this.newTodo.length > 0) {
                this.todos.push({
                    title: this.newTodo,
                    done: false
                })
            }
            this.newTodo = ""
        },
        deleteTodo(todo) {
            if (todo.done == true) {
                this.todos = this.todos.filter((item) => item !== todo);
            }
        },
    }
}
</script>
<style>
    .custom {
        width: 50%;
        margin: auto;        
    }
    .done {
        text-decoration: line-through;
    }
</style>