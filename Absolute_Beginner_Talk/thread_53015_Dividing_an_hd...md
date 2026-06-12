---
title: "Dividing an hd.."
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by Vurdak829 on 2005-07-29
I will explain myself in a better way :D
I have an hd (/dev/sda) that is divided in this manier:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2620       72292+  83  Linux
/dev/sda3            2621       10713    65007022+  83  Linux
/dev/sda4           10714       19929    74027520    5  Extended
/dev/sda5           10714       10838     1004031   82  Linux swap / Solaris
/dev/sda6           10839       19929    73023426   83  Linux
```
where in /dev/sda6 i have this ubuntu hoary. Cause 70Gb is too much for root on ubuntu, i want to divide /dev/sda6 in two ext3 partitions (/dev/sda6 and /dev/sda7) without losing data on /dev/sda6 (simply, i don't want to reinstall all the operating sistem) 'cause i wanna try another distribuition on the new partiton. How can i do that without losign my data?

---

### Post by heimo on 2005-07-29
gparted should be able to do that, as long as you can unmount the partition before resizing*

sudo apt-get install gparted
sudo gparted


EDIT: *) Of course that can be problem as the partition is / (root) - maybe you could do it using some live CD

---

### Post by Vurdak829 on 2005-07-30
[QUOTE=heimo]gparted should be able to do that, as long as you can unmount the partition before resizing*

sudo apt-get install gparted
sudo gparted


EDIT: *) Of course that can be problem as the partition is / (root) - maybe you could do it using some live CD[/QUOTE]

I hope that gparted is present on ubuntu live cd :D

---

### Post by heimo on 2005-07-30
[QUOTE=Vurdak829]I hope that gparted is present on ubuntu live cd :D[/QUOTE]

I'm pretty sure it's not part of Ubuntu Live CD. gparted is part of "universe" and it's not listed in package list for Ubuntu Live CD. I don't know if it's possible to install software* when you've booted using live-cd, but that's what I'd try - or another boot-CD.

*) temporarily in RAM or on separate HD partition

EDIT:
Check Knoppix 3.9 live-CD and QT-parted
[http://ubuntuforums.org/showpost.php?p=278600&postcount=3](http://ubuntuforums.org/showpost.php?p=278600&postcount=3)

---

### Post by Vurdak829 on 2005-07-30
[QUOTE=heimo]I'm pretty sure it's not part of Ubuntu Live CD. gparted is part of "universe" and it's not listed in package list for Ubuntu Live CD. I don't know if it's possible to install software* when you've booted using live-cd, but that's what I'd try - or another boot-CD.

*) temporarily in RAM or on separate HD partition

EDIT:
Check Knoppix 3.9 live-CD and QT-parted
[http://ubuntuforums.org/showpost.php?p=278600&postcount=3](http://ubuntuforums.org/showpost.php?p=278600&postcount=3)[/QUOTE]

Ok, i will check with knoppix. Thx :)

---

