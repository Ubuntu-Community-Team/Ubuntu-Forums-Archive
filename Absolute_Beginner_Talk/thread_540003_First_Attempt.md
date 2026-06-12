---
title: "First Attempt"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by mari0- on 2007-09-01
Well, I was about to install Ubuntu, and I got this error. I have been looking up some things about it, but nothing really pointing me in the right direction. From the looks of it I am guessing it is a problem with my graphics drivers? Anyways, here is some pics of the errors..maybe you guys can help? Please note, the installation hasn't even begun at this point it crashes  while loading the installation.

First: 
[http://i24.photobucket.com/albums/c1/mari0-/junk/DSCF3345.jpg](http://i24.photobucket.com/albums/c1/mari0-/junk/DSCF3345.jpg)

Then:
[http://i24.photobucket.com/albums/c1/mari0-/junk/DSCF3346.jpg](http://i24.photobucket.com/albums/c1/mari0-/junk/DSCF3346.jpg)

---

### Post by diatribe on 2007-09-01
what kind fo video card do you have?

---

### Post by mari0- on 2007-09-01
I don't have an actual video card, its ATI's on-board stuff :S 

ATI Radeon X1200 IGP or something >.<

---

### Post by southernman on 2007-09-01
Mind posting your /etc/X11/xorg.conf file?

---

### Post by mari0- on 2007-09-01
Sure, could you walk me through it though. o.O lol I don't even think I set one up, it does this soon as I hit install ubuntu.

---

### Post by mramsey on 2007-09-01
> I don't have an actual video card, its ATI's on-board stuff :S 

ATI Radeon X1200 IGP or something >.< 

Try [here]("http://ubuntuforums.org/showthread.php?t=414194"), I am having the same issue. The problem is the ATI X... series video. I have not completed my install yet but you will need to Down load the alternate install iso.

---

### Post by Tyke91 on 2007-09-01
to configure xorg.conf correctly, we should know what kind of driver you have and what bus it's plugged into


please open the recovery console and type

sudo lshw -businfo

---

### Post by mramsey on 2007-09-01
> **Tyke91 said:**
> to configure xorg.conf correctly, we should know what kind of driver you have and what bus it's plugged into


please open the recovery console and type

sudo lshw -businfo

The issue he's having is the same as mine...You can't get to the console because it hasn't installed anything yet.

---

