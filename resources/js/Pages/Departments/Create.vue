<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, useForm } from '@inertiajs/vue3';

const form = useForm({
    name:''
});

const closeForm = () =>{
    route('departments.index')
}

</script>

<template>
    <Head title="Create Department" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Create Department</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="p-4 bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <form @submit.prevent="$event => form.post(route('departments.store'))" class="mt-6 space-y-6 max-w-xl">
                        <InputLabel for="name" value="Department"></InputLabel>
                        <TextInput id="name" v-model="form.name" autofocus required type="text" class="mt-1 block w-full"></TextInput>
                        <InputError :message="form.errors.name" class="mt-2"></InputError>
                        <div class="flex justify-between">
                            <PrimaryButton :disabled="form.processing">
                                <i class="fa-solid fa-save"></i> Save
                            </PrimaryButton>
                            <!-- <button @click="closeForm" :class="'px-4 py-2 bg-gray-400 text-black border rounded-md font-semibold text-xs'">
                                <i class="fa-solid fa-cancel"></i> Cancel
                            </button> -->
                            <a :href=" route('departments.index') " 
                            :class="'px-4 py-2 bg-gray-400 text-black border rounded-md font-semibold text-xs'">
                                <i class="fa-solid fa-cancel"></i> Cancel
                            </a>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
