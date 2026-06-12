---
title: "No sound on Macbook Pro 17&quot;"
date: 2011-05-22
forum: Apple Hardware Users
---

### Post by FuturistCorporation on 2011-05-22
I have no sound on my macbook pro 17", intel core. I have searched and searched and have not found a solution. I have never yet had sound since I installed ubuntu. I am using 11.04 now. 

So far, I have edited the document /etc/modprobe.d/alsa-base.conf and added this line:
options snd-hda-intel model=mbp55, 
which did nothing.

Also ALSAmixer has all the channels turned up all the way except for S/PDIF

I don't think it is a hardware problem because when I play an MP3 file in VLC, in the visualization that would normally show the ups and downs of the sound playback, I get a flat line (not sure if that makes sense). 

I thought that Natty Narwhal came with all the sound drivers I would need already installed. Do I need to install Gstreamer?

---

### Post by FuturistCorporation on 2011-05-22
Failed to mention, I have a Macbook 3,1. Any help is greatly appreciated!

---

### Post by FuturistCorporation on 2011-05-22
found the solution here: [http://ubuntuforums.org/showthread.php?t=1299429](http://ubuntuforums.org/showthread.php?t=1299429)

Since it is mbp 3, 1 the line at the end of that file should have been options snd-hda-intel model=mbp3

:D

---

