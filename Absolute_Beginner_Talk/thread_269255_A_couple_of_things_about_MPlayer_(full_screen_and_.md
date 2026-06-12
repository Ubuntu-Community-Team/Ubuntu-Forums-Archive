---
title: "A couple of things about MPlayer (full screen and wmv)"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-10-01
I've been using mplayer for quite a while but there are some thing that just bug me...first of all: How the hell can i make mplayer play wmv files? and i don't mean 1 or 2...i mean ALL wmv files! cause i can play a couple of them, but not all.
Second of all, how can u make mplayer play movies in full screen? like .avi files, it's no fun watching a movie in a window with the size of a floppy disk, and i can't seem to activate the full screen option (i mean i can, but all it does is to resize the frame, but the movie stays in the same size)

any help (or other movie player names) would be welcome :) thanks

---

### Post by NESFreak on 2006-10-01
> **raul_ said:**
> (or other movie player names) would be welcome :) thanks

try xine

xine for totem:
```
sudo aptitude install totem-xine totem-xine-firefox-plugin
```

or an mplayer style xine frontend
```
sudo aptitude install xine-ui
```

---

### Post by skymt on 2006-10-01
For WMV support, install [w32codecs](https://help.ubuntu.com/community/RestrictedFormats).

For full-screen, it sounds like you have an issue with your mplayer video driver. If you use gmplayer (the mplayer GUI), open preferences (right-click the video for a menu) and try some different drivers (under the video tab). If you use the command-line version of mplayer, use the vo option, like this:```
mplayer -vo gl2,gl,xv,x11
```That will try two different OpenGL drivers (gl2, gl), then accelerated video (xv), then plain unaccelerated video (x11).

---

### Post by raul_ on 2006-10-05
got this from another thread, hope it helps:

---------------------------------------

just checked the Ubuntu repos and they do have a w32codecs packagage.

Since that didn't seem to work for you (are you really sure you enabled all repos?), I advice doing this the traditional(and always working) way.

Just copy and paste the following commands (this will always work for both Xine and MPlayer).

sudo mkdir /usr/local/lib/codecs/
sudo mkdir /usr/lib/win32

Next, download this codec package in your home map(just click on it): [http://www4.mplayerhq.hu/MPlayer/rel...060611.tar.bz2](http://www4.mplayerhq.hu/MPlayer/rel...060611.tar.bz2)
If Firefox downloaded it on your desktop, drag and drop it in your user's home map.

tar xvfj all-20060611.tar.bz2
sudo cp ./all-20060611/* /usr/local/lib/codecs/
sudo cp ./all-20060611/* /usr/lib/win32/

sudo chmod 755 /usr/local/lib/codecs/*
sudo chmod 755 /usr/lib/win32/*

Now it should simply play everything...

---------------------------------------------------

---

### Post by linuxmunky on 2006-10-05
VLC [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/) and you will never look back.  :)

---

