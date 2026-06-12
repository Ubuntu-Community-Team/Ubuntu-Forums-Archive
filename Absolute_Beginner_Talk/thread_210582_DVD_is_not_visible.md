---
title: "DVD is not visible"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by shivling on 2006-07-07
Music CDs play very well on my drive. But data DVDs do not.I install a DVD and no icon appears on desktop.

Got VLC media player installed. but cannot open dvd in it.

verified the following values in terminal. but doesn't help. 

shivkumar@shivkumar-desktop:~$ hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


shiv kumar

---

### Post by tommcd on 2006-07-07
When you say data DVD, do you mean a DVD +/-R? or a movie DVD? A data DVD (if it is a DVD you copied data onto yourself) should mount automatically and allow you to view the data.
For movies you need the codecs:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
scroll down to 'how to install DVD playback capability'.

---

### Post by Kashirigi on 2006-08-08
I'm having the same problem, including data DVDs that I originally burned with Breezy. My laptop has no such problems, although fstab and hdparm.conf are identical in both cases.

$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

---

### Post by orb9220 on 2006-08-08
Enable DMA on /dev/hdc: sudo hdparm -d1 /dev/hdc

---

### Post by Kashirigi on 2006-08-09
Well, I found the solution in my case. It wasn't that my settings had changed between Breezy and Dapper, it's that my DVD drive had crapped out, regardless of what OS I was using.  Buying another (better) drive solved all my problems, although the person who designed my case needs a smack in the head.

---

