---
title: "play windows media files on totem"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by rictus007 on 2006-10-19
Here is my problem.  I trying to stream windows media files (audio files) over the internet..from some radio station that I usually hear.  I'm trying to make totem (gstreamer) play this radio station but it said that I need the codecs.... I installed this codec w32codecs_20060611-1plf1_i386.deb wich make  mplayer to play windows video files but still can get totem to play nor audio or video from windows.

---

### Post by Iarwain ben-adar on 2006-10-19
Hi,
have you read the [sticky?]("http://ubuntuforums.org/showthread.php?t=182902")

> Install all the Windows codecs that you're use to:
sudo apt-get install w32codecs

This should do the trick ;)


Iarwain

---

### Post by moephan on 2006-10-19
There is another player called "mplayer" which you can install from the repositories. (Applications>Add/Remove and then search for MPlayer). You may find that you have better luck with this player.

---

### Post by Foudre on 2006-10-19
try video lan (aka vlc), they are supposed to support streams, and with the libraries you installed i beleive installed for xine then vlc should work, can't tell you how to use streams in it, never tried to, would love to broadcast stream though

---

### Post by Bigbluecat on 2006-10-19
Streamtuner.

Excellent for Streaming radio stations.

You can alwasys paste thestream into just about any media player. I've done this with both Amarok adn Listen.

---

### Post by Ashrael on 2006-10-19
For me: i had the same problem, i switched to totem xine and now everything works...maybe for you too, yeah i also installed the w32codecs...

---

### Post by rictus007 on 2006-10-19
Well, I will try Totem Xine and VLC which I already work with it under Windows (and it works). But here is my question...I install Totem xine and remove the gstreamer?

Mplyaer - play the wma that I have but some reason I can play audio from any radio station.

I try using automatix and it does not work eaither.

Thanks for all your coments...Ubuntu seems to be more easy than I though with this forum

---

### Post by ATAQ on 2006-10-19
Hey try using VLC Media Player
you can get it by adding:

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

to your repos list.

sudo gedit /etc/apt/sources.list

and then enable then in update information section of the system bar in gnome.

then: sudo apt-get update

sudo apt-get upgrade

I use VLC for everything. its class!

---

### Post by rictus007 on 2006-10-19
Ok...VLC works fine for hearing radio stations made for windows media player... but one last question.  How I can make that everytime that I clic on a mms://whateverradiostation ... instead of open this link usin totem, it use vlc to play the files

---

