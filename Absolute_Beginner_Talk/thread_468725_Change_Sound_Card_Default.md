---
title: "Change Sound Card Default"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-06-09
I just installed the latest kernel upgrade today and ....  the sound stopped working.  I have a SoundBlaster Live card installed.  

I ran alsamixer and it shows the default card to be Intel ICH5.

I ran  asoundconf list
 and it reports - 

Names of available sound cards:

ICH5

SAA7134

Live


What I would like to know please is how to change the default sound card from ICH5 to Live.

---

### Post by overdrank on 2007-06-09
> **expatCM said:**
> I just installed the latest kernel upgrade today and ....  the sound stopped working.  I have a SoundBlaster Live card installed.  

I ran alsamixer and it shows the default card to be Intel ICH5.

I ran  asoundconf list
 and it reports - 

Names of available sound cards:

ICH5

SAA7134

Live


What I would like to know please is how to change the default sound card from ICH5 to Live.

Hi if I am not mistaken you can go to system, preference, sounds, sounds tab and select the default card from the drop down menu. Hope this helps good luck!:D

---

### Post by expatCM on 2007-06-09
I have accidentally just found a solution which worked for me .....

sudo asoundconf set-default-card Live

Had to log out to get it to have effect but .... it did .....

---

### Post by kazik on 2007-06-11
I can't really speak for GNOME. Under KDE you cannot choose the card in Control Center (all you can choose there is whether you want to use ALSA, OSS, ESD, TOSS or whatever). But **asoundconf** works great and it's changes are local. 

```

$ asoundconf list
Names of available sound cards:
I82801BAICH2
PLTDA60
$ asoundconf set-default-card I82801BAICH2

```

...then simply restart the application you want to use, e.g., Kaffeine, Rythmbox, amarok, Totem... 
[ actually Kaffeine needs a full restart, but Rythmbox needs just stop -> play ]

Works like charm with my setup (Intel on-board + Plantronics headset). I can play different music simultaneously on both cards :D

BTW: do it _without sudo_ -- the changes are local to user (in ~/.asoundrc) and that's really enough!

---

