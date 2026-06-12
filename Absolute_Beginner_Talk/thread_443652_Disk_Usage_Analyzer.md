---
title: "Disk Usage Analyzer"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-05-14
I don't know the best way to ask this so tell me if I'm unclear.

I have an external hdd of 250 gb and an internal hdd that's 60 gb. I attempted to set up a partition on the external hdd so that a 100 gb had linux and 150 gb was still usable with windows. Looking at the disk usage analyzer, it says I have 183.7 gb available. Is there a way to check and see each drive that's available and how much space is available on each one? I think I might have done something stupid on the install so I need to check this.

Again, I'm a noob and I tried to make as much sense as possible.

---

### Post by PMatt on 2007-05-14
I might as well just add what stupid thing I think I did.

After I set the computer up to dual boot, I got an error 21 message(means disk could not be found). I went to try and either reinstall or remove Ubuntu from the external hdd to try again. The installer on the disk did not work because I got an error when trying to just install ubuntu for the entire disk, and I was only given the option to partition with the 150 gb that I intended to be left for windows. I went into the gnome partitioner and tried to just delete the part with linux on it and then suddenly everything worked fine I didn't get the error 21 message (maybe I accidentally deleted the part with windows...).

So basically, I think I just have either 100 or 150 gb of unusable space on my external drive right now.

---

### Post by MoxJet on 2007-05-14
There are various ways to do this. If you're using gnome (normal ubuntu windows manager) start this program using the terminal:
```
gnome-system-monitor
```
Go to the File Systems tab and you should see nice percentage bars for each partition mounted.

---

### Post by MoxJet on 2007-05-14
If you want a functional graphical (GUI) partition editor try gparted,
```
sudo apt-get install gparted
```
It should make you able to create, delete, edit, usw partitions.

(if you need to do it via terminal try fdisk or cfdisk. read their man-pages: man fdisk)

---

### Post by PMatt on 2007-05-14
Thanks, I think I did mistakenly delete the Windows portion instead of the Ubuntu portion like I had intended because the drive works with Linux but not when I boot up windows(I guess this fixed the problem for me too, lol). 

So now I just have to figure out how to get the drive to work with windows or figure out how to make the entire drive work with ubuntu. Chances are I'll probably have another question about this in a week or so :) 

Thanks again.

---

