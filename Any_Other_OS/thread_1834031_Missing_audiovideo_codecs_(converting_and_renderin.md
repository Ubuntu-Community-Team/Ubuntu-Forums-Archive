---
title: "Missing audio/video codecs? (converting and rendering video problems.)"
date: 2011-08-26
forum: Any Other OS
---

### Post by ryandushane on 2011-08-26
I have recently been using Transmageddon and WinFF for converting video. Also, i have been using OpenShot, and Kdenlive for video editing. The video will not convert, and OpenShot and Kdenlive will not render in h.264. OpenShot said that the h.264 codecs needed to be installed, but i went and checked in the synaptic package manager and they were already installed. Also, the converting worked for a while when i first installed the programs... I am usually pretty good with Linux but this has me stumped. 
Also, i am using Linux Mint, but essentially its the same thing as Ubuntu. 
PLEASE HELP!

---

### Post by BicyclerBoy on 2011-08-27
The H264 encoding in ffmpeg uses libx264 & this has to be compiled in..
I think this means compiling it yourself.
I think the standard Ubuntu repos ffmpeg does not do H264 encoding.

What did you install via synaptic ?

Medibuntu repository is assumed..
mplayer, WinFF HandBrake are built on ffmpeg. You need the libav*-extras packages.
Transmaggedon is built on gstreamer. You will need the gstreamer good, bad & ugly lib set.

---

### Post by thewolfman on 2011-08-27
If you haven't already done it, install the "medibuntu" repo!!.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Regards Wolfman:P

---

### Post by ryandushane on 2011-08-27
@BicyclerBoy
Yes I installed it via synaptic. I have this problem many times before. I do not believe that you have to compile it.

---

### Post by BicyclerBoy on 2011-08-28
Note that with each ubuntu distro upgrade the medibuntu repository is disabled.
There is an install/setup script for adding medibuntu.

Medibuntu gets you all the gstreamer packages (good bad ugly) & the unstripped libav*-extras packages.
libav* are the core shared libraries of ffmpeg.
The H264 encoder x264 (libx264) can be used stand-alone or is called from ffmpeg to do H264 encoding.

---

### Post by Perfect Storm on 2011-08-28
Moved to Other OS/Distro talk.

---

