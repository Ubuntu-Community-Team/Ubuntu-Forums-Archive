---
title: "Problem with SBlive"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Riiktar on 2006-01-28
Okay I posted before about my conextant/riptide soundcard.  Well I got a soundblaster live from a friend today.  I popped it in and Ubuntu does see it, however there is no sound.  

0000:00:09.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 5
        I/O ports at d000 [size=64]
        Capabilities: <available only to root>

is there a patch I can DL and run or does anyone have some step by step help to run in terminal?   I know I am asking a lot but I promise I have also been learning a lot.  Thanks for any help!

---

### Post by Mission 10 on 2006-01-28
Try this:

Go to applications/sound and video/volume control

Select Edit/Preferences, and make sure that analog front is checked and/or other speakers you may have. 

This made me crazy for a long time before I figured it out. Hope it works for you.

---

### Post by Riiktar on 2006-01-28
GAhh No luck.  No front option either.  I have tried alsamixer in term and all with no luck.  Now I did have a SB 64AWE ISA card in before I got the Live donation, but I had to put in a sudo code everytime to use it.  I am going to cry, I just want sound.

---

### Post by Riiktar on 2006-01-28
NOTE:  I just tried to open a video in mplayer and this error kept flashing

Unable to find simple control PCM

---

### Post by Mission 10 on 2006-01-28
Do you have onboard sound also?

---

### Post by Mission 10 on 2006-01-28
PS See if you have another option via System> Preferences> Sound. If so select it and then do the above recommendation.

---

### Post by Riiktar on 2006-01-28
I have no onboard.  Now I some how screwed up gnome-volume-control so that it is stuck on 3d and some crap GAHHHH.  I dont even know anymore.  Ubuntu reads the card in every program.  Nothing is muted.  I just dont get it.

---

### Post by Mission 10 on 2006-01-28
Bunk card?? Sorry that's the extent of my knowedge on sound cards. One of the "gurus" should be more help.

---

