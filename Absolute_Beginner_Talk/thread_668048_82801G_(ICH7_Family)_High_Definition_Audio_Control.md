---
title: "82801G (ICH7 Family) High Definition Audio Controller mic not working"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by djmrman on 2008-01-15
Hi

I am having troble getting a 82801G (ICH7 Family) High Definition Audio Controller microphone working it plays sounds alright but for the life of me I can't get to mic to work I have managed to get the mic under windows working but needed to use asus sound mixer to do it as the windows one didn't work. I am guessing it is the same problem here. 


Can anyone help a newbie

---

### Post by BandD on 2008-01-15
I don't know if you've looked through these threds yet, but they may help:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

[http://ohioloco.ubuntuforums.org/showthread.php?t=530374]("http://ohioloco.ubuntuforums.org/showthread.php?t=530374")

I also googled and found, this don't know if will help or not:

[http://www.linux-on-laptops.com/forum/showthread.php?t=1488]("http://www.linux-on-laptops.com/forum/showthread.php?t=1488")

I don't have this particular chip set, I've got an Intel ICH6 family and had some trouble with the mic.  I finally got it working by editing /etc/modprobe.d/alsa-base with an option where model=acer (even though I'm on a Sony Vaio).  

Goodluck!

---

