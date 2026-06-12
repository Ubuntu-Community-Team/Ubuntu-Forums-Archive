---
title: "failed grub install fatal error"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Techboy_Miata on 2007-06-12
im attempting to unstall Ubuntu to my IDE drive while redirecting the placement of the grub to my SATA drive however i keep getting Grub could not be installed to x place (locations ive tried 
sda0 and sda1)
ive also tried to get info about how i would need to phrase this from fdisk -l but i get nothing

if anyone knows exaticly how to phase this so the installer understands it would be wonderful.

if i didnt love Ubuntu so much and see great things in this new live ver i would've gave up on it by now

---

### Post by dstew on 2007-06-12
Grub disk names are (hd0), like that. For example, the first partition on the first disk is (hd0,0). That might be the equivalent to the Linux partition name /dev/sda1.

If you want to install the grub boot loader to the Master Boot Record (MBR) of a disk, you give it just the disk name, (hd0) for example.

It can be a little tricky to figure out exactly what names grub is using. There are techniques to use if you are totally lost.

---

