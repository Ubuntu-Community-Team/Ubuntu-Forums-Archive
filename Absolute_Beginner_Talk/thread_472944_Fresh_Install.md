---
title: "Fresh Install"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-06-13
I have a kubuntu 6.10 installation on my PC at the mo and want to change to Ubuntu 7.04; I'm thinking a clean install is the way to go. But my friend installed the kubuntu for me so I'm not sure what partitions are for what on the hard drive (there seem to be 4 or 5).

Secondly, my files from my windows (boo hiss) are on a seperate partition on the same disc; would doing a clean install risk damaging them? There is a lot (approx 50GB) so backing up would take a long time but I'll do it if it seems likely my data will be otherwise damaged.

Is a clean install the way to go or is there another way?

---

### Post by limelightos on 2007-06-13
you should be ok as long as you don't wipe the ntfs partitions like i did first time

---

### Post by Nekiruhs on 2007-06-13
Well, Ubunty's partition would be ext3, and windows partition would be ntfs, and most others should be fat32. The only way you might damage those files, is if you accidentaly install Ubuntu over them.

---

### Post by limelightos on 2007-06-13
and you probs don't want to wipe the fat32 ones either

---

### Post by terabite on 2007-06-13
Well.. while installing just take care that you dont install on vfat(fat32) or NTFS... thats it...

Keep 'swap' as it is.
Format parition with filesystem type ext3.. and set mount point as '/'

That shud do it...

---

### Post by ahaslam on 2007-06-13
Why not just do:
```
sudo aptitude install ubuntu-desktop
```
See 'Ubuntu Tutorials' in my sig for more (inc. removing kde) ;)

---

