---
title: "[SOLVED] audacity"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-10-29
i installed audacity via synaptic
the edit commands don't work nor the buttons and when i tried to save a file to mp3 it error you don't have a dependency library.
in the forums it says i need many dependencies.
how can i get this to work i need to put someof my cassettes to mp3's i used to do it easy with sound forge and edit easily.
help?????

---

### Post by Baby Boy on 2007-10-29
You need to install Lame to export to .mp3.

> sudo apt-get install liblame-dev

---

### Post by john262 on 2007-10-29
I installed the Lame codec but when I try to get Audacity to export a WAV file to MP3 it still doesn't offer MP3 as a file type that I can export to. Does anyone know how to troubleshoot this? Thanks.

---

### Post by DezSP on 2007-10-29
The -dev package won't do you much good. Add liblame instead.

---

### Post by Pumalite on 2007-10-29
Synaptic>Search>lame>lame>install

---

### Post by DarinB on 2007-10-29
i installed lame via synaptic it still doesn't work.
do i need more dependencies???

---

### Post by Pumalite on 2007-10-29
Are you sure you installed Audacity through Synaptic?. Synaptic resolves all dependencies on installation of ALL programs. If not, it tells you it cannot do it.

---

### Post by Crafty Kisses on 2007-10-29
Sounds like you installed it using Automatix.

---

### Post by DarinB on 2007-10-30
i don't have automatix on my machine heard it was a disaster.
i did install it via synaptic and i checked by attempting to install each dependency  individually and it came up already installed.
today i tried again to use it and it actually cut and edited but it wouldn't open the mp3 library lame to save it.
it seems hit or miss as to what is going on with it.
i closed the program reopened it and then the edit tools wouldn't work.
it is simple install a program via synaptic install lame via terminal (as above) edit a simple mp3 podcast.
i don't know why this is so difficult??
any ideas maybe i don't know how to cut and paste or put the cursor on the music and drag it then click the scissors.
very frustrating help??

---

### Post by DarinB on 2007-10-30
i got the edit tools to work but when i try to save project as tehn go to mp3 encoder  it says save as lame.so then it says can't open mp3 encoder install libmp3lame i already installed lame via synaptic and lame extras
what now???

---

### Post by Pumalite on 2007-10-30
You have to point to Audacity where the lame file is.

---

### Post by DarinB on 2007-10-30
pumalite how do i do that?

---

### Post by DarinB on 2007-10-30
OK i think i got it to work. when audacity asked to find libmp3lame.so i looked for it in filesystem and found in usr/lib/libmp3lame.so.0 and libmp3lame.so.0.0 i changed the choice in the search window to libmp3lame.so.0 it loaded and it seems to work for now. i will let you know if i can record from my cassette player then i will be able to do what i need. thank you all
if anybody thinks this will cause a problem let me know.

---

