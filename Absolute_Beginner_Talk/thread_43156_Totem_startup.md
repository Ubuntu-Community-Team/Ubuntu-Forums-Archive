---
title: "Totem startup"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by chrisndebb on 2005-06-20
Hello, new to Ubuntu here. When I try to play a video, Totem tries to start but fails due to an error that reads,"Resource busy or not available , As far as I can tell Totem for xine and gstreamer is installed. Any suggestions?
Chris

---

### Post by chrisndebb on 2005-06-21
I could really use some help on this. Anybody have anything to offer?
Thanks in advance,
desperate Chris

---

### Post by poofyhairguy on 2005-06-21
[QUOTE=chrisndebb]Hello, new to Ubuntu here. When I try to play a video, Totem tries to start but fails due to an error that reads,"Resource busy or not available , As far as I can tell Totem for xine and gstreamer is installed. Any suggestions?
Chris[/QUOTE]

Try to use Gxine. I always have problems with totem.

> sudo apt-get install gxine

run it by using the command "gxine"

---

### Post by chrisndebb on 2005-06-21
Won't let me install Gxine. I get the error message on the command line, "E: Couldn't find package gxine"    Thanks...Chris

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=chrisndebb]Won't let me install Gxine. I get the error message on the command line, "E: Couldn't find package gxine"    Thanks...Chris[/QUOTE]


Do exactly what this says to do:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

type in this command afterwards:

> sudo apt-get update

then try to install gxine.

---

### Post by TravisNewman on 2005-06-22
mplayer is also a good alternative. I use it almost all the time, until there's the one in a hundred file it won't play, then I try out gxine. It usually won't play there either though ;)

To simplify things, you can install totem-xine, so that you change totem's back end from gstreamer to xine.

The choices are near endless.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=panickedthumb]mplayer is also a good alternative. I use it almost all the time, until there's the one in a hundred file it won't play, then I try out gxine. It usually won't play there either though ;)
[/QUOTE]

Then only one thing will work. VLC

[http://packages.ubuntu.com/hoary/gnome/gnome-vlc](http://packages.ubuntu.com/hoary/gnome/gnome-vlc)

---

