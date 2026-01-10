# 🎵 MoodMusic
MoodMusic è un’applicazione web che genera playlist Spotify basate sul **tuo umore** oppure sul **meteo reale della tua città**.  
Un progetto semplice ma d’impatto, pensato per rendere la musica più personale, contestuale e divertente.
## 🌟 Funzionalità principali
### 🎧 Playlist basate sul Mood
L’utente può scegliere tra 4 stati d’animo:

- 😄 **Felice**
- 😌 **Relax**
- 😔 **Triste**
- ⚡ **Carico**

Ogni mood è collegato a playlist Spotify curate e già pronte.
### 🌦️ Playlist basate sul Meteo
Inserendo una città, l’app:

1. Recupera il meteo reale tramite **OpenWeather API**
2. Analizza temperatura e condizioni atmosferiche
3. Imposta automaticamente una “vibe” tra:
   - ☀️ `sunny`
   - 🌧️ `rain`
   - ❄️ `cold`

La playlist finale è una combinazione di **Mood + Meteo**, ad esempio:
## ▶️ Player Spotify integrato
La playlist scelta viene caricata direttamente in un **iframe Spotify**, pronta per essere ascoltata senza uscire dall’app.
## 🧠 Logica del sistema
### 🔍 Analisi Meteo
La vibe viene determinata così:
- Temperatura **< 5°C** → `cold`
- Codice meteo **< 700** → `rain` (pioggia/neve)
- Altrimenti → `sunny`

### 🎼 Scelta Playlist
Una volta selezionato il mood:

```js
const key = `${mood}_${currentVibe}`;
const playlistId = playlists[key];

