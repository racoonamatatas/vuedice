<template>
    <div>
        <table style="border-collapse: collapse; width: 10%; margin: 0 auto">
            <tbody>
                <tr style="border-bottom: 2px solid black">
                    <th>Getal</th>
                    <th>Aantal</th>
                </tr>
                <tr>
                    <td>1</td>
                    <td>{{ faceCount['1'] }}</td>
                </tr>
                <tr>
                    <td>2</td>
                    <td>{{ faceCount['2'] }}</td>
                </tr>
                <tr>
                    <td>3</td>
                    <td>{{ faceCount['3'] }}</td>
                </tr>
                <tr>
                    <td>4</td>
                    <td>{{ faceCount['4'] }}</td>
                </tr>
                <tr>
                    <td>5</td>
                    <td>{{ faceCount['5'] }}</td>
                </tr>
                <tr>
                    <td>6</td>
                    <td>{{ faceCount['6'] }}</td>
                </tr>
            </tbody>
        </table>
    </div>
    <div>
        <button @click="rollDice(nThrows)" id="gooi" type="button">Gooi!</button>
    </div>
</template>

<script setup>
import {reactive} from 'vue';

const nFaces = 6;

const nThrows = 6;

// returns a random number on the interval [1, numberOfFaces].
const randomDiceNumber = numberOfFaces => Math.floor(Math.random() * numberOfFaces + 1);

const faceCount = reactive({
    1: 0,
    2: 0,
    3: 0,
    4: 0,
    5: 0,
    6: 0,
});

function rollDice(totalThrows) {
    // The counts need to be reset to 0.
    for (const key in faceCount) {
        faceCount[key] = 0;
    }

    for (let idx = 0; idx < totalThrows; ++idx) {
        faceCount[randomDiceNumber(nFaces)]++;
    }
}
</script>
