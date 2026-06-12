---
title: "Mac-Ubuntu USB problems"
date: 2012-01-06
forum: Apple Hardware Users
---

### Post by aMeltz on 2012-01-06
Hi, I tried installing Ubuntu by USB so I followed the instructions online and the USB failed to boot. I will try with a disk next time but then my mac said it could not read the USB. I tried it on my windows side and I was able to reformat it, however it now states its capacity is around 750 MB where its supposed to be 8 GB. Is there anyway I can fix my USB so it is back to normal?

---

### Post by 2F4U on 2012-01-06
Is there more than one partition on the usb? For me it looks as if the installation of the liveCD created a 750 MB partition on the usb and the rest is in a second partition or not allocated.

---

### Post by 2F4U on 2012-01-06
With respect to your boot problems my experience is was the same when I installed on a MacBook from 2008. It refused to recognize the usb as a bootable media. However, it booted fine from a liveCD.

---

### Post by aMeltz on 2012-01-06
> **2F4U said:**
> Is there more than one partition on the usb? For me it looks as if the installation of the liveCD created a 750 MB partition on the usb and the rest is in a second partition or not allocated.

In Disk Utility to the left it shows my usual partitions, then it says "8.02 GB Lexar USB Flash Drive Media" and underneath it obviously indented "NO NAME". However there is only one indentation so I think there is only one partition. What I believe is the way it is formated only allows for up to that much, since it is in MS-DOS (FAT) the problem is getting it back to a format that can support the fill 8 GB.

---

### Post by 2F4U on 2012-01-06
What happens if you remove the 750 MB partition? Do this only if you don't need it any more! When it has been removed, create a new partition covering the whole available space and format it. You should be able to do this from the Windows machine.

---

### Post by aMeltz on 2012-01-06
I did on my mac side (sorry was kinda low on time didn't want to restart) and I managed to get it up to 7.6 GB! Thanks for the help, I'll try it on my Windows side.

---

