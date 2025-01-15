<script>
    import { Sound } from "svelte-sound";
    import k1 from "../assets/amsterdam.wav";
    import k2 from "../assets/kharab.wav";
    import k3 from "../assets/ravana.wav";
    import h1 from "../assets/harami.mp3";
    import h2 from "../assets/vitas.mp3";
    import h3 from "../assets/yasu.mp3";

    const h1Sound = new Sound(h1);
    const h2Sound = new Sound(h2);
    const h3Sound = new Sound(h3);

    const k1Sound = new Sound(k1);
    const k2Sound = new Sound(k2);
    const k3Sound = new Sound(k3);
    const sounds = [k1Sound, k2Sound, k3Sound];
    const hsounds = [h1Sound, h2Sound, h3Sound];

    let currentSound = null;

    function stopCurrentSound() {
        if (currentSound && currentSound.stop) {
            currentSound.stop();
        }
    }

    function hPlay() {
        stopCurrentSound();
        const randomNumber = Math.floor(Math.random() * hsounds.length);
        const randomSound = hsounds[randomNumber];
        currentSound = randomSound;
        randomSound.play();
    }

    function kPlay() {
        stopCurrentSound();
        const randomNumber = Math.floor(Math.random() * sounds.length);
        const randomSound = sounds[randomNumber];
        currentSound = randomSound;
        randomSound.play();
    }
</script>

<style>
    .container {
        display: flex;
        height: 100vh;
        background: linear-gradient(to bottom, #ff7e5f, #feb47b);
    }

    .button {
        flex: 1;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2rem;
        font-weight: bold;
        color: #fff;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        cursor: pointer;
        background-color: #6a11cb;
        border: 2px solid #2575fc;
        transition: transform 0.2s ease, background-color 0.3s ease;
    }

    .button:hover {
        background-color: #2575fc;
        transform: scale(1.1);
    }

    .button:active {
        transform: scale(0.95);
        background-color: #1a69d4;
    }
</style>

<div class="container">
    <div class="button" on:click={hPlay}>
        🎵 Harami
    </div>
    <div class="button" on:click={kPlay}>
        🎶 Kharab
    </div>
</div>
