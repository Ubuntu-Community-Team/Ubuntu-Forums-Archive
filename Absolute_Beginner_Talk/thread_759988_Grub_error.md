---
title: "Grub error"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by hoobadoo on 2008-04-19
I had ubuntu installed on my second hard drive but recently reformatted it because I needed the extra space for music and other things. After I reformatted the hard drive and I tried to boot up, grub started and then it said error 17 and just sat there. Right now im using an ubuntu live CD and any help would be appreciated.

---

### Post by bodhi.zazen on 2008-04-19
what operating system are you running and what partition is is located in ?

---

### Post by hoobadoo on 2008-04-19
I'm using windows xp and its the only os on there, it hasn't been partitioned. Linux was on my second hard drive which I reformatted and set up for use in windows again.

---

### Post by bodhi.zazen on 2008-04-19
You will need to restore the windows boot loader.

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by hoobadoo on 2008-04-20
Ok, I tried your thing that you posted on how to redo the boot from linux and now I don't get the grub error 17...but instead the load screen for my computer comes up and just keeps restarting over and over again...all I can do is go into bios or pick where to boot from. The only boot that works is from a CD.

---

### Post by jpyanowski on 2008-04-20
Use Super GRUB Disk to remove GRUB. XP should take over. Is the disk that had Ubuntu on it been set as slave?

---

### Post by sandysandy on 2008-04-20
yes there is a utility called super grub disk - SGD  for short ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) or ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

u can download it and burn it as iso image. then u can boot from the bootable CD and use the various options which r self explanatory. u can fix MBR of windows XP or Linux etc.

heres a tutorial on Super Grub.

[http://users.bigpond.net.au/hermanzo...bdiskpage.html](http://users.bigpond.net.au/hermanzo...bdiskpage.html)

what u can do is boot in SGD and restore windows MBR

regards

---

