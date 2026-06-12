---
title: "probs with sound plz help"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by McGriff on 2007-09-12
i installed Ubuntu 7.04 and in the beginning i had probs with the ati driver after a weekend of troubleshooting and stress i got it working now only to discover that i now have NO SOUND whatsoever i am completely new to ubuntu and i followed a few guides given on the forums so far i used the console to determine if my hardware was picked up and it was its a  ALC880 and i think intel was in front of that so i went to the website and got the linux driver and installed them and it appeared everything went ok but still no sound plz help as i am tired of troubleshooting this and wish  to get this resolved 
thanks in advance 
McGriff:confused:

---

### Post by Maestro23 on 2007-09-12
Open a terminal and type:

> alsamixer

You should see a bunch of sliders.  Make sure nothing is muted.

Use arrow keys to move and the "M" key will toggle Muting.

---

### Post by McGriff on 2007-09-12
yep tried that bro and they are all fine

---

### Post by McGriff on 2007-09-12
--bump--
plz guys anyone there that can help resolve this if you want more infor on my system etc etc just ask i really really want to get this sorted so i can be done with xp as im tired of having to duel boot to watch dvd/music etc etc 

HELP ME OBI-WAN YOUR MY ONLY HOPE                          :lolflag:

Just checked the device manager and its detected my sound devise there so this has to be something simple im just really new to linux so i dont know what else to try

---

### Post by Hospadar on 2007-09-12
Is this like built-in-to-the-motherboard sound?   Do you know your motherboard model or the chipset?

---

### Post by McGriff on 2007-09-12
since there is very little intrest in my question at the moment im gonna post all the info i have HOPING someone may find this useful and know how to help


i have a laptop fujitsu siemens amilo xi 1546 and i installed ubuntu 7.04 
It detects my sound card but unfortunately i cant hear anything...
the specs for my laptop's soundcard are: azalia codec (7.1 via SPDIF).
WIth the help of 'hwbrowser' i can see that ubuntu recognized the card as:
Intel Corporation 82801G (ICH7 Family) High Definition AUdio Controller
and the driver: snd-hda-intel
anyone knows how to fix this?
thanks  again

---

### Post by j0lliyo on 2007-09-15
sorry i can't help you got the same issue on an amilo la 1703. detecting hardware and everything, but no sound

---

### Post by tyler22 on 2007-09-15
I had a no sound issue on my toshiba laptop, but the problem was corrected after installing the ubuntu updates after a fresh install. Have you done that?

---

### Post by McGriff on 2007-09-19
ok i haven't tried a reinstall just yet thats the last step i suppose but since nothing else has come up to try i might as well give it a shot.
 The thing is most ppl on the forums are really nice and helpful and they give me links to treads like this [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) which is helpful but the reason im posting in the Absolute Beginner Talk forum is because i am just that a beginner and those guilds dont leave alot of room for ppl who dont understand them (ie) me so if anyone else wants to help me please put you help in steps i could then try 

thank you all again

---

### Post by McGriff on 2007-09-22
ok ive reinstalled and it detects the sound card no problem AND I CAN HEAR SOUND THROUGH MY EAR-PHONES but not through the laptop main speakers. i have brought up alsa mixer and made sure nothing wasnt muted:confused: i know im so close to solving this problem PLZ PLZ someone help

---

### Post by gagatz on 2008-01-20
you might have tried this, but anyhow, there is this project on
opensound.com
where you can download and install a complete package of sound drivers, which worked for me and others (amilo 1703). If the tar.gz doesn't work try the .deb version, and check for the correct kernel with

uname -r

good luck.

---

### Post by j0lliyo on 2008-03-25
[http://amilola1703.uprize.no](http://amilola1703.uprize.no) <-- there you can see how to install the alsa drivers for this computer, witch should resolve your sound issues

---

