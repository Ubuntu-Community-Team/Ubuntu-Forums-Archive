---
title: "VLC segmentation fault when opening mkv files"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-05-24
Whenever I try to open a .mkv file on Ubuntu 5.10, it crashes. Then only thing stated in the terminal is "segmentation fault".

I tried this on a fresh install also, with no success. What can I do?

Please don't tell me to use mplayer or other player. I could do that, but VLC states it can play mkv files, so it should play them. Could this be a bug?

LATER EDIT: Here's a discussion on the VideoLAN forums, regarding my issue:

[http://forum.videolan.org/viewtopic.php?t=13520&highlight=mkv](http://forum.videolan.org/viewtopic.php?t=13520&highlight=mkv)

It appears that the VLC package in the Breezy repos might be compiled without mkv support. It this is true, compiling vlc from source would allow me to play mkv files in VLC? Or should I use the vlc packages in the breezy-backports?

The initial question is still standing.

---

### Post by Beej on 2006-05-24
I believe you are correct, VLC is not compiled with mkv support in breezy. Compiling it from source would sort this out, but you would have to compile it qwith the correct options. I havent done this myself but ./configure --help from the source directory normaly gives the configure options. once you know which ones you want try 

./configure --option1 --option2

then make then make install or checkinstall.

Alternatively, if you want to see if there is something is wrong with the file, I can recommend Geexbox. This is a live cd media player based on mplayer (only 6mb download) it supports mkv and plays just about anything on any hardware.

---

### Post by zugu on 2006-05-24
There are so many people having this issue, just look at the VLC forums. And nobody's answering them. I know, I know, the developers aren't to provide free techincal support at any hour in the day, I'm just saying that there should be some "I can't play mkv files, build me again, properly this time" message before crashing. I just found out that the needed flag is *--enable-mkv*.

And what was the reason for building the breezy-main VLC binaries without mkv support? Someone please enlighten me.

And how about the breezy-backports VLC binaries? Are they built with mkv support or not?

---

### Post by Beej on 2006-05-24
I would suggest installing the matroska libs suggested inthe link you posted , and then compiling from source from the VLC website with the flags you mentioned before.

Don'y get too upset, VLC is pretty cool, and matroska is a pretty random avi wrapper.

---

