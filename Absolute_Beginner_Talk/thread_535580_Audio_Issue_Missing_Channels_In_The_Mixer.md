---
title: "Audio Issue: Missing Channels In The Mixer"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by E_K on 2007-08-26
So, i haven't got it quite as bad as alot of other people around here, i have sound from the internal speakers, but the intergrated mic doesn't work, which doesn't bother me too much, but there are some audio jacks on the front of the laptop (Acer Extensa 5210) it uses the dreaded Realtek 268 chip, i believe the lack of fuctionality is because in the alsa mixer there are only 2 channels, there is nothing for mic, headset etc. This came to my attention as i was following a How To on installing the alsa drivers. which all seemed to install fine. I couldnt find this problem i did a few different searches on this site and google, but all leading to people having the no sound problem, which i tried a few solutions but none worked, one actualy completly disabled the sound card,which wasnt so good :confused:

Any of you guys got any ideas on getting the missing audio channels working, or getting the jacks to work?

If you need me to post anything just let me know.

---

### Post by albesan on 2007-08-26
hey,

have you tried typing on a terminal:  alsamixer   

See what you find in there and make sure the channels you need aren't muted and up. 

hope this helps.

a

---

### Post by E_K on 2007-08-26
all i have is master and PCM, no other channels i can show

---

### Post by E_K on 2007-08-30
bump

---

### Post by E_K on 2007-09-01
Come on guys please help, someone must know a solution to this or a vauge idea of something i could at least try, ive tried everything i can think of reinstalling drivers, adding patches, googling every word i can think of relating to the subject.... please help i really need to use the jacks on the laptop

---

### Post by E_K on 2007-09-03
bumpitty bump bump, i also searched in synaptic, and there was an update for the kernal ended in .31 and i was using .29, after the update it wouldnt detect my sound card, as i am not to familiar with the linux business yet so i just reinstalled everything again

---

### Post by E_K on 2007-09-12
come on guys..... please help

---

### Post by MrHippocampus on 2007-09-12
running alsamixer in a terminal as albesan suggested will show you all of the channels alsa knows about, you might have to press left/right arrow to go through them all and also press tab to go through the capture devices.

If what you want isn't there then its a problem with the alsa driver, you could try running a gusty livecd and see if alsa in the gusty kernel works.

---

### Post by E_K on 2007-09-14
i know about the alsamixer, the other channels simply are not seen.

Where is a reliable place to download the gutsy cd image

---

### Post by MrHippocampus on 2007-09-14
[heres]("http://www.ubuntu.com/testing/tribe5") a link for the latest gusty livecd/installer. Remember its still under heavy development and using it is at your own risk etc.....

---

### Post by rine238 on 2007-12-03
I have the same problem. I have too Acer Extensa 5210, and Kubuntu 7.04, and I have only master and PCM channel for sound. I want only headphones channel enable if it is possible anyway, but I don't know what to do. I can't listen music all the time at laptop's speakers.:(

---

