---
title: "I just don't understand mount point!"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ve3rpm on 2007-09-23
I've just installed a second HDD and can't seem to use it.  Admittedly this is not the first time that I have run into a lot of issues with the mount point or for that matter the puter telling me that I don't have permission to try a myriad of things.  I've searched for hours, so perhaps there is just something I'm missing.  If you could explain the mount point, file system and mount options, perhaps I can overcome this problem.  I gotta tell you ubuntu makes me feel like I should get the front seat on the short bus!  If you know what I mean.  thanx Dan

---

### Post by szymon_g on 2007-09-23
if this second disk is a sata drive, ubuntu should see it as /dev/sdb and /dev/sdb1,2,3 <- depands how many partitions it has.
mounting points are folder in system where partitions will be mounted in (something like C: D: or E in ms/windows): you can set mounting points for any directory inside / (but the most common place is /mnt or /media)

to mount it you have to write:

sudo mount -t vfat /dev/sdb1 /mnt/win/c

vfat = virtualfat = fat32 = usually used in dos-based windows
/dev/sdb - your partition (but it will vary on your system: you have to check it)
/mnt/win/c - a dir. where the partition will be mounted (before mounting you have to create partition- sudo mkdir)

if this drive is not removable you should consider adding it to /etc/fstab file for automounting (so you won't have to mount it manually)

---

### Post by ve3rpm on 2007-09-23
Yes it's a sata and it's right in front of me when I bring up computer.  I just don't have permission to mount it.  I don't have windows and I gparted it to fat 32.  When I go to properties, should I not be able to set the place to mount it?  If it needs something done in the terminal, why give me the option of picking a place to mount it to under properties/ volume?

---

### Post by szymon_g on 2007-09-23
Yes it's a sata and it's right in front of me when I bring up computer. I just don't have permission to mount it. I don't have windows and I gparted it to fat 32. When I go to properties, should I not be able to set the place to mount it? If it needs something done in the terminal, why give me the option of picking a place to mount it to under properties/ volume?

check 

ls /dev/

it should give you (some) information - look for files like sdb sdb1 -- these are files of your's disc' partitions.

try to do that:
sudo mkdir /mnt/c
sudo mount -t vfat /dev/sdb[1,2,3] /mnt/c

using command 'sudo' is essential.

/dev/sdb[1,2 etc] are partitions- if your first disc is also sata, it (should) be represented as /dev/sda[1,2,3] (to bee sure look on /etc/fstab).

you can add something like that into your /etc/fstab

/dev/sda1       /mnt/some_name            vfatt    defaults              0       0

for more info look here [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by ve3rpm on 2007-09-23
K, thanx I'll mull all of this over and see what I can figure out.  I'll read through the link you so kindly offered... it is one that I haven't seen before.  thanx. Dan

---

### Post by szymon_g on 2007-09-23
good luck :P

---

