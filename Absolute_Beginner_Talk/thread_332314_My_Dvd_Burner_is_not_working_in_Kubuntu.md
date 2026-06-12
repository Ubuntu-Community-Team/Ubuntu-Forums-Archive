---
title: "My Dvd Burner is not working in Kubuntu"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2007-01-05
I have a Pioneer DVR 111-D that works perfectly in Windows.  When I try to burn in linux, I get this error (with k3b)
[http://img100.imageshack.us/img100/3220/snapshot2nv2.png](http://img100.imageshack.us/img100/3220/snapshot2nv2.png)
[img]http://img100.imageshack.us/img100/3220/snapshot2nv2.png[/img]
any suggestions
I just got the burner, it is set to master, as was the burner that i had before that was working under the very same setup.

---

### Post by Shatrat on 2007-01-05
Well, it may be that DMA is not enabled on that drive.  You can check by typing ```
hdparm /dev/hdc
``` in a terminal window to see the drive settings, assuming hdc is your disk drive.  You might have to alter the last letter.

It might also be that you need to run it as root, due to the guy who wrote the cd recording utilities for linux being something of a power tripper.

---

### Post by %hMa@?b&lt;C on 2007-01-05
> **Shatrat said:**
> Well, it may be that DMA is not enabled on that drive.  You can check by typing ```
hdparm /dev/hdc
``` in a terminal window to see the drive settings, assuming hdc is your disk drive.  You might have to alter the last letter.

It might also be that you need to run it as root, due to the guy who wrote the cd recording utilities for linux being something of a power tripper.

i already tried using DMA, havent tried as root yet, but it works as a regular user on my old burner same exact setup

---

### Post by %hMa@?b&lt;C on 2007-01-05
> **jeffc313 said:**
> i already tried using DMA, havent tried as root yet, but it works as a regular user on my old burner same exact setup

i may just reinstall ubuntu tomorrow if necessary

---

### Post by %hMa@?b&lt;C on 2007-01-07
still doesnt work after fresh amd64 Kubuntu install
any suggestions??? It works perfectly in Windows

---

### Post by %hMa@?b&lt;C on 2007-01-07
bunp... still having the same problem 
hpdarm reports
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

---

