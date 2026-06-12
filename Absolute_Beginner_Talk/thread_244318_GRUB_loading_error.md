---
title: "GRUB loading error"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Demetrios on 2006-08-26
I am imaging a 200 gig HHD, everything appears to have loaded correctly until this error 

The error happens after the system is loaded and the CD is removed for a boot.

GRUB Loading stage 1.5
Grub loading, please wait....
Error 18

Help

---

### Post by lynxus on 2006-08-26
Ive seen similar errors,

Grub needs to be installed at the BEGINNING of the partition ( summat like first 1024 blocks ) or along those lines. Otherwise it wont load.

You could try a live cd and use a partition manager to assist ?

Try a google lookup for grub error18 


Hope this points you in a fairly helpful direction

---

### Post by malachakla on 2006-08-26
I have the same exact problem... I know absolutely nothing about partitioning, how do I add the boot partition, and where in the installation process?
Thanks!

---

### Post by nickpaton on 2006-08-26
Have a look at this:

[http://www.ubuntuforums.org/showthread.php?t=43061]("http://www.ubuntuforums.org/showthread.php?t=43061")

---

### Post by uph0ria on 2006-08-26
"Error 18: Selected cylinder exceeds maximum supported by BIOS"

I've encountered this problem many times. What I did was boot up the disk partitioner on the "Breezy Badger" install CD, and resized my ext3 partition to something a little smaller. 

Example: 40 Gig HDD :resized--->29 Gig HDD

That's what fixed Error 18 for me, good luck!

---

