---
title: "Macbook Pro 3,1 nothing opens and out of SW-IOMMU space"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by quicksilver21098 on 2008-11-06
I recently upgraded to 8.10 from 8.04 on my mbp 3,1. I did it through the update manager. Now whenever I start it up nothing opens. Ubuntu starts up fine but when I try to open anything the window comes up but nothing appears in the window, its blank. Also, whenever I shut down lines start running down the screen saying "Out of SW-IOMMU space at 4224" and I have no idea what that means. Lastly, this all seemed to start when right after it had finished updating and I restarted it asked me about the status thing in the upper right corner and if I wanted to change it to the new status thing, I said yes and then it said to log out to complete the changes, right when I did that is when I got the SW-IOMMU error.

I'm kinda new to linux so I really have no idea what I'm doing and I couldn't start to diagnose the problem anymore than what I've already said so hopefully someone else knows what's going on lol

Thanks for your help

---

### Post by cyberdork33 on 2008-11-07
Upgrades are generally buggy. You should do a fresh install.

---

### Post by blindmouse on 2008-11-07
I'm having this same problem on a MacBook Pro 3,1 as well - on fresh installs of 8.10.  
For the first several minutes of a session, windows draw correctly.  After a few minutes, new windows appear without their contents - no text, widgets, images, etc (in any application).

Anyone have any ideas?

Thanks..!

---

### Post by cyberdork33 on 2008-11-07
can you post the output of 'demsg'

---

### Post by blindmouse on 2008-11-07
Sure thing, the output is many lines of:

```
[ 2356.977686] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.080041] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.182469] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.284827] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.387233] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.489644] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.592042] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.694451] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.796841] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2357.899373] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.001634] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.104008] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.206411] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.308823] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.411248] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.513568] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.616020] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.718365] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.820778] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2358.923211] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.025567] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.127997] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.230406] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.332768] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.435170] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.537547] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.639971] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.742351] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.844735] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0
[ 2359.947135] DMA: Out of SW-IOMMU space for 4224 bytes at device 0000:0b:00.0

```


I did notice something when I tried to pipe this output to a file - my filesystem is now read-only.  I'm booted off of the third partition on my internal disk, formatted as ext3, with no swap partition.  

I can also post the full output of dmesg if that is helpful...

---

### Post by cyberdork33 on 2008-11-07
I believe this is a kernel error with your SATA controller... This affects other distros too:
[http://forum.mandriva.com/viewtopic.php?t=98840](http://forum.mandriva.com/viewtopic.php?t=98840)


Bug report seems to be here:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/267089](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/267089)

---

### Post by blindmouse on 2008-11-07
Thanks so much for your help!  I'll check this out now.

---

