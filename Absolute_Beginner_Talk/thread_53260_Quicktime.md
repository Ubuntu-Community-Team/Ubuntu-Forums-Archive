---
title: "Quicktime"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by cadaver on 2005-07-30
When I try to stream a Quicktime video, I get video but no audio. What gives?

---

### Post by royg1234 on 2005-07-30
see if this helps - [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by pataphysician on 2005-07-31
if you get sound with everything except quicktime movies, try installing totem-xine via synaptic. it's the only player that i get audio from with .mov files.

---

### Post by jctosu on 2007-08-15
I dont think the totem version works as well as the mplayer version, here is how to install the mplayer version:

install the following packages, you may need to enable the medibuntu repos [(http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php"))

mplayer
mplayer-firefox
win32codecs
libquicktime
gstreamer ffmpeg
gstreamer gl
gstreamer plugin base
gstreamer plugin good
gstreamer plugin bad
gstreamer plugin ugly
gstreamer plugin bad multiverse
gstreamer plugin ugly multiverse


Search for vlc plugin for firefox.

DO NOT INSTALL IT.

If it is already installed, uninstall it.

Mplayer plugin seems to work much better, especially for QT format, and vlc plugin will take priority over mplayer in firefox.

(For someone who wants to manually uninstall vlc plugin, it's in /usr/lib/firefox/plugins)



Now hit Alt+F2 add copy in the following:

Quote:

gksudo gedit /etc/mplayer/codecs.conf

In the menu go to Search-->Find

type in "ffsvq3" and hit ok

comment out the paragraph so it looks like this:

Quote:

#videocodec ffsvq3

# info "FFmpeg Sorenson Video v3 (SVQ3)"

# status working

# fourcc SVQ3

# driver ffmpeg

# dll svq3

# out YV12,I420,IYUV

save the document



and restart firefox!


worked for me on most quicktime files, not all files work for me but a lot of them do

---

### Post by misfitpierce on 2007-08-15
If you want program to auto config everything it is listed in my sig. Automatix loads music programs, internet programs, codecs etc.

---

