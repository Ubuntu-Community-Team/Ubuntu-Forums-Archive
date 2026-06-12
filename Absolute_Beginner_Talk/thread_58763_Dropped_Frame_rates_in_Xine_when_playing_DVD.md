---
title: "Dropped Frame rates in Xine when playing DVD"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-21
Hi,
I did everything ubuntuguide.org mentioned in setting up Xine.
I installed it and it's working. Playing my dvds. 
But I get an error message and the video is laggish.

"The amount of dropped frame is too high, your system might be slow, not properly optimised or just too loaded."

how do I fix this? please

---

### Post by jasmuz on 2005-08-21
Please verify that you have enabled DMA for that DVD device.

If so, look under xine's options...and check what is the output selected for video.

---

### Post by ROUBOS on 2005-08-21
I cant find that option...

---

### Post by jasmuz on 2005-08-21
Left click on the screen, settings ->setup  ->Video

---

### Post by TristanMike on 2005-08-21
In case you don't know to see if DMA is on from a terminal....

sudo hdparm /dev/hdc

Assuming that your DVD drive is "hdc", I check device manager under the Advanced tab, but there must be a command line alternative, but I don't know what that would be.

---

### Post by ROUBOS on 2005-08-21
Xine keeps freezing up,
how do I kill the process... I used to do it in unix back in 1995... 
don;t remember though :(

Is MPlayer better? should I be installing that instead?

---

### Post by jasmuz on 2005-08-21
[QUOTE=ROUBOS]Xine keeps freezing up,
how do I kill the process... I used to do it in unix back in 1995... 
don;t remember though :(

Is MPlayer better? should I be installing that instead?[/QUOTE]
 Mplayer is very good actually....i use it for DVD playback and Xine for Avi

---

### Post by ROUBOS on 2005-08-21
It apears like I dont have DMA or other ipmortant files...

I get this:

$ hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

---

### Post by jasmuz on 2005-08-21
As i figured, you have DMA not enabled....
read here how to enable it : [http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)

---

