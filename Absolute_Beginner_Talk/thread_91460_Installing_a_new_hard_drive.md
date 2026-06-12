---
title: "Installing a new hard drive"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by herrpoon on 2005-11-17
Hi, I'm trying to install a new hard drive which I got today.  I'm following this guide [https://wiki.ubuntu.com/InstallingANewHardDrive?highlight=%28drive%29%7C%28hard%29](https://wiki.ubuntu.com/InstallingANewHardDrive?highlight=%28drive%29%7C%28hard%29) 
I've physically installed the hard drive and I'm pretty sure it's detected by the BIOS but when I type "dmesg | less" into the terminal I can't see any references to any hard drives, and am not sure what I'm doing wrong.  Any help would be much appreciated.

Many thanks,  Herrpoon

---

### Post by schdefan on 2005-11-17
Hi!
You can see if your harddisk is recognized by ubuntu by typing 
```
cat /proc/partitions
``` in the terminal.
If you connect the HD as slave on the first controller it should show hda for the first HD and hdb for your new one. 
You need to format with a filesystem and edit /etc/fstab as well to be able to use the partition.
schdefan

---

### Post by herrpoon on 2005-11-17
Ahha!  Magic!  Just what I needed, many thanks :smile:

P.s Do you think I should partition it into two or leave it as one, its a 160Gb hdd by the way.

---

### Post by schdefan on 2005-11-17
Depends on what you want to do. If it is just for storage then i suggest just use one big partition. Or maybe create a small partition (5GB) to have some space for experiments left or as backup for your system!
If you can describe what you want to do, one can give more suggestions.
schdefan

---

### Post by herrpoon on 2005-11-17
I just left it as one big partition, I suppose I can always split it up later if I need to.  Once again, many thanks for your help, I have it all working now!

---

