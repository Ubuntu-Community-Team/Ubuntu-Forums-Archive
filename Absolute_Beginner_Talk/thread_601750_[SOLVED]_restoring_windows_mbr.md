---
title: "[SOLVED] restoring windows mbr"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-11-03
hi guys

i need to restore MBR of my windows xp hdd which has been overwritten by GRUB.
i have backup of 446 bytes of the MBR. can someone tell me the command to restore it.

(system specs Pentium D 3.0GHz, 1GB RAM, 160 GB SATA hdd(Win XP) 40GB IDE HDD (Gutsy) 

thanx

---

### Post by Pumalite on 2007-11-03
Boot from XP CD, hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by meierfra on 2007-11-03
Pumalite's method should work. To use your backup:

sudo dd if=full_path_of_your_back_up  of=/dev/sda bs=1 count=446

Sorry for getting you in this mess.

---

### Post by sandysandy on 2007-11-03
> **meierfra said:**
> Pumalite's method should work. To use your backup:

sudo dd if=full_path_of_your_back_up  of=/dev/sda bs=1 count=446

Sorry for getting you in this mess.

thanx for the help.

i restored the MBR on my Win XP hdd and could boot up into win xp again.

i used the command as follows:-

sudo dd if=/home/ubuntu/03novbackupdevsdb-mbr of=/dev/sdb bs=446

(where 03novbackupdevsdb-mbr is my backup of MBR) 

regards

---

