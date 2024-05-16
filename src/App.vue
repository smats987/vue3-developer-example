<template>
    <app-layout>
        <section class="w-11/12 mx-auto py-8">
            <h1 class="text-2xl mt-8 mb-2 font-bold">Welcome</h1>
            <p class="my-4">
                This project is for a developer example to test and learn using
                vue 3 composition API and tailwind. See
                <a
                    class="text-blue-600"
                    href="https://tailwindcss.com/"
                    target="_blank"
                >
                    https://tailwindcss.com/
                </a>
                and
                <a
                    class="text-blue-600"
                    href="https://vuejs.org/"
                    target="_blank"
                >
                    https://vuejs.org/
                </a>
                .
            </p>
            <p class="my-4">
                The goal here is to create a modal popup box that is on the top
                layer of the DOM using the teleport elements. It will also need
                to have content passed throught to it via a vue slot.
                <br />
                You may see a similar functionality in the AppNotification.vue
                file.
            </p>
            <h2 class="text-xlg mt-8 mb-2 font-bold">App Notification</h2>
            <p class="my-4">
                The App Notification functionality uses a few key components to
                make it work.
            </p>
            <h3 class="text-lg mt-8 mb-2 font-bold">Slot</h3>
            <p class="my-4">
                The slot vue functionality allows us to pass through vue
                components/html elements to the AppNotification component.
            </p>
            <p class="my-4">
                <a
                    class="text-blue-600"
                    href="https://vuejs.org/guide/components/slots.html"
                    target="_blank"
                >
                    https://vuejs.org/guide/components/slots.html
                </a>
            </p>
            <h3 class="text-lg mt-8 mb-2 font-bold">Expose</h3>
            <p class="my-4">
                We can hook into the AppNotification functions by exposing the
                functions within. Within the AppNotification I am exposing the
                function "openNotification" that allows us in this file to run
                that funciton. You can get the AppNotification component
                variable by referencing it by using the Vue Functionaly "ref".
                The "const notification = ref(null);" gets the component with
                the "ref="notification"" attribute. We can then reference this
                and run the function by running
                "notification.value.openNotification();"
            </p>
            <p class="my-4">
                <a
                    class="text-blue-600"
                    href="https://vuejs.org/guide/essentials/template-refs"
                    target="_blank"
                >
                    https://vuejs.org/guide/essentials/template-refs
                </a>
            </p>
            <h3 class="text-lg mt-8 mb-2 font-bold">Teleport</h3>
            <p class="my-4">
                The Vue teleport tab allows us to move elements from their
                locaitons with the vue structure to another location within the
                DOM.
                <br />
                The benefit for the functionality of the modal is that we can
                place it on the top level of the DOM allowing us to make it on
                top of all other components and not constrained within a group
                of elements.
                <br />
                Looking at the AppNotification again we can see that we are
                calling the component within this file here. Without the
                teleport it would appear with &#60;section&#62; tag on line 3.
                With the teleport we can move the AppNotification to be inside
                another element. In this case the '#teleport-bottom-right' (by
                default).
            </p>
            <p class="my-4">
                <a
                    class="text-blue-600"
                    href="https://vuejs.org/guide/built-ins/teleport.html"
                    target="_blank"
                >
                    https://vuejs.org/guide/built-ins/teleport.html
                </a>
            </p>
            <h3 class="text-lg mt-8 mb-2 font-bold">
                Examples of functionality
            </h3>
            <p class="my-4">Tooltip (No Tailwind)</p>
            <p class="my-4">
                <a
                    class="text-blue-600"
                    href="https://codesandbox.io/p/sandbox/tooltip-hover-9gfylm?file=%2Fsrc%2Fcomponents%2FTooltip.vue"
                    target="_blank"
                >
                    https://codesandbox.io/p/sandbox/tooltip-hover-9gfylm?file=%2Fsrc%2Fcomponents%2FTooltip.vue
                </a>
            </p>
            <p class="my-4">Simple Modal (No Tailwind)</p>
            <p class="my-4">
                Here is a simple modal if you want to see an example of how it
                might be done.
            </p>
            <p class="my-4">
                <a
                    class="text-blue-600"
                    href="https://codesandbox.io/p/sandbox/tooltip-hover-forked-cgsfnj"
                    target="_blank"
                >
                    https://codesandbox.io/p/sandbox/tooltip-hover-forked-cgsfnj
                </a>
            </p>
            <app-notification ref="notification" variant="info">
                Inline Notification
            </app-notification>
            <div class="my-2">
                <app-button @click="handleOpenNotification">
                    Open Notification
                </app-button>
            </div>
        </section>
    </app-layout>
</template>

<script setup>
import AppLayout from '@layouts/AppLayout.vue';
import AppNotification from '@components/notifications/AppNotification.vue';
import AppButton from '@components/buttons/AppButton.vue';
import {inject, onMounted, ref} from 'vue';

const notification = ref(null);
const handleOpenNotification = () => {
    notification.value.openNotification();
};
</script>
