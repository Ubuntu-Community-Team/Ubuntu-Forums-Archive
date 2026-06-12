---
title: "Media player problems"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by pumpkinpatch on 2007-06-29
I can't get any of my media players ie. Rhythem box, Amarok, VLC, Totem to play movies or music.  I have installed w32 codecs, gstreamer, and mysql.  What am I missing?

---

### Post by happysmileman on 2007-06-29
> **pumpkinpatch said:**
> I can't get any of my media players ie. Rhythem box, Amarok, VLC, Totem to play movies or music.  I have installed w32 codecs, gstreamer, and mysql.  What am I missing?

Well Amarok uses the Xine engine... So you'd install the Xine extra plugins for that... Dunno if that'd solve your problem but it supports most music and movie formats and Amarok automatically uses whatever codecs Xine has...

Should support some movie formats as well

---

### Post by into_311 on 2007-06-29
what formats are the files you are trying to play in? ie. mp3, avi, ogg, aac, mpg, etc.

Have you installed all the  gstreamer plugins? there is several plugins required to playback all your content.

---

### Post by pumpkinpatch on 2007-06-29
I'm playing mp3, mp4, ogg, ogm, and dvd's.  none work.

---

### Post by RomeReactor on 2007-06-29
Hi. For mp3 in Rhythmbox, you need to install **gstreamer0.10-plugins-ugly** (and maybe it's multiverse variant, **gstreamer0.10-plugins-ugly-multiverse**). For the video files in totem, I recommend you install **totem-xine** and its libraries (libxine1, libxine-extracodecs, libxine1-ffmpeg);  Look for those on Synaptic (System-->Administration-->Synaptic Package Manager). Or, from the terminal (Applications-->Accessories-->Terminal):
```
sudo apt-get install totem-xine libxine1 libxine-extracodecs libxine1-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
For DVDs, you need the [Medibuntu repositories and libdvdcss2]("https://help.ubuntu.com/community/RestrictedFormats#head-17f9569280643c3d657d7df670f44c448c95c4fb"). From the terminal:
```
gksudo gedit /etc/apt/sources.list
```
and look for this entry:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Add it if it's not there already, save the file and close Gedit; now open Synaptic and press the Reload button on the top left. After it finishes reloading the package information, search for libdvdcss and install **libdvdcss2, libdvdnav4, libdvdplay0,** and **libdvdread3**. When that's done, open a terminal and enter:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

