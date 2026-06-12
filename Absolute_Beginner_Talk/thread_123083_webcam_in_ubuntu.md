---
title: "webcam in ubuntu"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by bartbes on 2006-01-29
I have installed drivers for my webcam (Logitech Quickcam Messenger) with EasyCam. But I can't do something with it maybe it's because of my PCTV card (Pinnacle PCTV Rave), can anyone pls help me with this?? Tried several programs and I use the ibmcam driver, just can't get it to work

---

### Post by Inkyskin on 2006-01-29
I followed this to get my QC Messenger working:

[http://www.ubuntuforums.org/showthread.php?t=111225&highlight=quickcam+green](http://www.ubuntuforums.org/showthread.php?t=111225&highlight=quickcam+green)

---

### Post by bartbes on 2006-01-29
thx that worked  :D

---

### Post by patrick295767 on 2006-01-29
[QUOTE=bartbes]I have installed drivers for my webcam (Logitech Quickcam Messenger) with EasyCam. But I can't do something with it maybe it's because of my PCTV card (Pinnacle PCTV Rave), can anyone pls help me with this?? Tried several programs and I use the ibmcam driver, just can't get it to work[/QUOTE]
  
I got same problems.... Exactly, & never made it ! Good Luck !

Regards

---

### Post by bartbes on 2006-01-31
[quote=Yoriko]- Grab the latest sources from Here
- Install the kernel-headers 2.6.10 for i386 from synaptic, and the kernel sources.
- apt-get xawtv if you don't already have it
- apt-get gcc-3.4 if you don't have it, and gcc

-extract the drivers; type into the terminal "export CC=gcc-3.4"

- if you havn't already, set root password "sudo passwd"

-run quickcam.sh, it shouldn't give any errors until "Can't detect webcam"
-Keep ignoring errors after that one~
- run "sudo modprobe quickcam"
- have fun
[/quote]

What isn't working? It worked fine for me...

---

