---
title: "Flash Drive"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-08-06
Kubuntu or ubuntu is not recognizing my flash drive. I plugged it in right but it isnt recognizing it. Is it supposed to show up on my desktop?

---

### Post by Zedd on 2007-08-06
What are the outputs of "lsusb" and "sudo fdisk -l"?

---

### Post by Istonian on 2007-08-06
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         608     4883728+  82  Linux swap / Solaris
/dev/hdc2             609        9729    73264432+  83  Linux

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes

   Device Boot      Start         End      Blocks   Id  System

For sudo fdisk i

---

### Post by Zedd on 2007-08-07
For now, install pmount, then run "sudo pmount /dev/sda" This is assuming that sda is your 1GB flash drive. 

Beyond that, I'm not sure what to do. You may want to file a bug report on launchpad.

---

### Post by sailor2001 on 2007-08-07
if you have several usb ports, one or 2 maybe usb1 and the other usb2.......some flash sticks will not work on usb1

---

### Post by Inxsible on 2007-08-07
Zedd is right. Use pmount to mount it. Look at the link in my signature on a small how to

---

### Post by Zedd on 2007-08-07
Pmount is only a temporary solution, although it will work. Automounting should work. I'm having the same problem with Gutsy. It always worked for me in Feisty though. See [http://ubuntuforums.org/showthread.php?t=516814](http://ubuntuforums.org/showthread.php?t=516814)

You may want to check to make sure kded is running. If it's off automount definitely will not work.

---

### Post by Inxsible on 2007-08-07
> **Zedd said:**
> Pmount is only a temporary solution, although it will work. Automounting should work. I'm having the same problem with Gutsy. It always worked for me in Feisty though. See [http://ubuntuforums.org/showthread.php?t=516814](http://ubuntuforums.org/showthread.php?t=516814)

You may want to check to make sure kded is running. If it's off automount definitely will not work.

what do you mean its a temporary solution?

I have mounted 5 of my external drives with pmount and they are mounted everytime i connect them.

---

### Post by joe.turion64x2 on 2007-08-07
Did your flash drive automounted normally before?

---

### Post by Zedd on 2007-08-08
*Any* flash drive should be automatically mounted regardless of whether it has been pmounted before. Pmounting is a temporary solution because there should be a way to fix the system so that it will automatically mount any flash drive.

---

### Post by joe.turion64x2 on 2007-08-08
We had a similar problem in Fedora 7 before, check this: [http://www.fedoraforum.org/forum/showpost.php?p=840424&postcount=61](http://www.fedoraforum.org/forum/showpost.php?p=840424&postcount=61)

I assume the device is recognized by the system (you can use *sudo gparted* to find out).

Joe.

---

