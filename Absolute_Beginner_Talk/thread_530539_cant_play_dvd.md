---
title: "cant play dvd?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by gaddo on 2007-08-20
Can anyone help with a problem playing dvds on 6.06Lts.
I have downloaded Gxine but i get a Red light on the set up wizard "Check For MIT Xv extension" What is it and how to i get it?
Thanks gaddo:confused:

---

### Post by Gone fishing on 2007-08-20
I don't know if others consider it a cheat or risky but I just download automatix and then use it to download all the codecs and also download mplayer and vlc.

---

### Post by Hobo Joe on 2007-08-20
Install VLC player.

```

sudo aptitude install vlc

```

---

### Post by gaddo on 2007-08-20
Thats for that but still wont work?
It might help if i explain in more detail.
I now 3 dvd players Totem Movie Player,gxine and Vlc media player.
The Totem which i have installed the following packages
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
libdvdread3
And get this error

"Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it."

 Gxine gives the following error "MPEG Block"
and lastly Vlc media player just hangs
Gaddo

---

### Post by abba567 on 2007-12-23
Just bumping this to see if anyone has found a fix, thanks

---

### Post by khughitt on 2007-12-23
try:

**sudo aptitude install libdvdcss2**

---

### Post by buzzmandt on 2007-12-23
try:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by SOULRiDER on 2007-12-23
[https://help.ubuntu.com/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/ubuntu/desktopguide/C/video.html)

Take a look at the playing DVD section.

---

### Post by billgoldberg on 2007-12-23
I don't know if this will work for ubuntu 6.06 but it worked for me on Gutsy.

It's a little program that will install all the proper dvd codecs (and allot more too).

check this link:
[http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart](http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart)

---

