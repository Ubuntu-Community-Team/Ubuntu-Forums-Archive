---
title: "010101 after 64 bit install"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by smacintyre569 on 2007-08-21
On my AMD 64 bit machine, 64 bit Live cd worked fine. 
Once at the live cd desktop I clicked the install button. 
Ubuntu installed with no errors. 

After reboot my display runs:
 010101010101010101010101010101010 over and over and over until I hit the break key.

Any ideas?

---

### Post by milosz.galazka on 2007-08-21
Hello

Please post results of  **sudo fdisk -l /dev/sda** where /dev/sda is hard disk with installed ubuntu, It could be /dev/sda or maybe /dev/hda ...

Grub uses files in /boot directory on your main partition (if you didn't created small partition for /boot). Maybe these files are not in first 8Gb of hard disk (but it doesn't matter with hardware produced in recent years) so maybe you installed system on extended partition? If yes then just try installing ubuntu on primary partition and check it out...

---

