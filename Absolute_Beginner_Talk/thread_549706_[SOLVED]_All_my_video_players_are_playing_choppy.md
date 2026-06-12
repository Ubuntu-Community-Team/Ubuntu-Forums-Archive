---
title: "[SOLVED] All my video players are playing choppy"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-12
Both my Mplayer and my VLC player are streaming very choppy from the apple.com/trailers page. Has anybody else run into this?

---

### Post by mikeyphi on 2007-09-13
This guide might help: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I haven't been right through it but it seems to touch on your issue.

---

### Post by Perfect Storm on 2007-09-13
you properly need to install libdvdcss2 
You can get it through mediabuntu, just follow the link that mikeyphi provided, it will tell you how.

---

### Post by cwrann on 2007-09-13
This is what I got when I tried to download libdvdcss2 

home@home-desktop:~$ sudo apt-get install libdvdcss2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libfuse2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It looks like I already had it which I had thought because I used to be able to play online video.

I have an AMD 64 so I tried the 64 version of libdvdcss

home@home-desktop:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_amd64.deb
(Reading database ... 138018 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2+build1 (using libdvdcss2_1.2.9-2medibuntu2+build1_amd64.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu2+build1) ...

I get the same results as before. Do I need to reinstall mplayer and vlc?
I just installed compiz fusion does that have anything to do with it?

---

### Post by cwrann on 2007-09-21
It looks like I had a couple of things going wrong. I got rid of the VLC plugin, I installed gstreamer gl from synaptic and I got rid of media player connectivity. 
I think that Media Player Connectivity was not allowing the computer to buffer the video clips far enough out to make them watchable, and wasn't saving them in temporary files so that I could wait for the entire clip to load before viewing.
Without Media Player Connectivity the browser was shutting down when I tried to play QT, presumably, because I had VLC selected for quicktime files but mplayer set as the prefered overal media player.
or maybe it was all because I didnt have gstreamer gl installed.

---

