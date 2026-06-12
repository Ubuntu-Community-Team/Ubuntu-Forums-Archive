---
title: "[arxius.ape] eina"
date: 2007-07-19
forum: Catalan Team
---

### Post by prostata on 2007-07-19
si us plau, com puc convertir arxius.ape a mp3????

Gràcies

---

### Post by RainCT on 2007-07-19
Hola,

Insta&#320;la el paquet "nautilus-script-audio-convert" i el codec "lame":

```
sudo apt-get install nautilus-script-audio-convert lame
```

I executa això a la terminal per tal d'activar el script insta&#320;lat:

```
nautilus-script-manager enable ConvertAudioFile
```

Un cop fet això, reinicia el Nautilus (tanca la finestra i torna-la a obrir). Fes unn clic amb el botó dret sobre l'arxiu de so en questió i veuras que, sota d'"Obre amb", t'haurà aparegut una nova opció: "Seqüències". D'allà, se&#320;leciona "ConvertAudioFile" i t'apareixerà un programa amb interfície gràfica on podràs convertir l'arxiu al format que prefereixis.

---

### Post by prostata on 2007-07-20
> **RainCT said:**
> Hola,

Insta&#320;la el paquet "nautilus-script-audio-convert" i el codec "lame":

```
sudo apt-get install nautilus-script-audio-convert lame
```

I executa això a la terminal per tal d'activar el script insta&#320;lat:

```
nautilus-script-manager enable ConvertAudioFile
```

Un cop fet això, reinicia el Nautilus (tanca la finestra i torna-la a obrir). Fes unn clic amb el botó dret sobre l'arxiu de so en questió i veuras que, sota d'"Obre amb", t'haurà aparegut una nova opció: "Seqüències". D'allà, se&#320;leciona "ConvertAudioFile" i t'apareixerà un programa amb interfície gràfica on podràs convertir l'arxiu al format que prefereixis.

Moltes gràcies, la seqüència ConvertAudioFile, que apareix només permet convertir a format .wav  no hi ha altre opció de format d'arxiu disponible...¿es normal??

salutacions

---

### Post by prostata on 2007-07-20
he seguit aquest procediment, per tal de fer la conversió:

A) he passat d'ape a .wav
B) amb soundconvert de .wav a .mp3

En cap cas funciona, quan el reprodueixo amb amarok o vlc amb qualsevol altre fa un só "d'oli fregit"

Teniu alguna suggerència??

---

### Post by RainCT on 2007-07-21
Prova insta&#320;lant els paquets que sugereix, a veure:

```
sudo apt-get install lame vorbis-tools flac faac faad mplayer
```

---

### Post by prostata on 2007-07-22
> **RainCT said:**
> Prova insta&#320;lant els paquets que sugereix, a veure:

```
sudo apt-get install lame vorbis-tools flac faac faad mplayer
```

així ho he fet, però els formats de conversió que m'apareixen son:
ogg/flac/acc/wav...hauria de sortir també mp3???

---

### Post by prostata on 2007-07-23
A synaptic diu el següent sobre l'script audio-convert:

A nautilus audio converter script
audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE,
AAC, and WMA files. It has an easy-to-use interface that makes it possible to
fill in the tags for a few formats, copy the tags from input files into the
new files, and choose the quality of compression.

Com és doncs que un arxiu(s), en format.ape no en surt l'opció de convertir-lo a format mp3??, ¿me estic perdent algun pas?? o és que definitivament no puc amb aquest script convertir un format dels acceptats comunment a mp3??

salut

---

