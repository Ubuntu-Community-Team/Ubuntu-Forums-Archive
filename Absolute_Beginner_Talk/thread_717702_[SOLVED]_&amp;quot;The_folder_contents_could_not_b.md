---
title: "[SOLVED] &amp;quot;The folder contents could not be displayed&amp;quot; Help my external hardrive!"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by philosophicscience on 2008-03-07
I'm running Ubuntu 7.10 on an Acer Aspire 5670. I have a seagate 250 gig external. When I first installed Ubuntu, everything worked fine with the harddrive. Now it's sitting on the desktop but when I try to open it I get the error message:

The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Hippocampus".

The power did cut off at my house recently, and I remember getting an error about the external during the outage. I really need the files on my harddrive... am I boned?

---

### Post by Fixman on 2008-03-07
```
ls -A Desktop
``` and post the results.

---

### Post by philosophicscience on 2008-03-07
micah@brain:~$ ls -A Desktop
untitled folder
micah@brain:~$

---

### Post by oedha on 2008-03-07
how bout sudo fdisk -l  ?

---

### Post by philosophicscience on 2008-03-07
micah@brain:~$ sudo fdisk -l
[sudo] password for micah:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf8550f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

---

### Post by oedha on 2008-03-07
hmmm.....your external 250 is un-seen......
what if you unplug and plug it again.........and try to run sudo fdisk -l again.....

---

### Post by philosophicscience on 2008-03-07
I did a reboot, and some strange happenings. First, I blackscreened and had to hard reboot. Then after a long boot up time, my desktop comes up with the harddrive on it, and I can access all the files. 

Problem solved, sorry guys.

---

