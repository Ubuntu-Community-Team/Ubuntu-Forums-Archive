---
title: "Aother Mounting new NTFS drives"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by crunchyfox on 2007-01-25
hello there i m have the same problem as conradcliff from his"Mounting new NTFS drives" Thread and i checked out the link he found and i still cannot mount the drive, it is a data only drive has never had an os installed on it.... i have a copy of knoppix that mounts it automatically.... so here we go 

sudo fdisk -l results for the drive :
Device       Boot       Start      End    Blocks           Id  System
/dev/hdb1   *            1          2490   20000893+   7    HPFS/NTFS

sudo mkdir /media/windows
everything was ok at this point

sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
this bought up a HOWTO on the mount command.....

read through it.....but couldnt see what i did wrong....
do i also need to put the info in the fstab file before mounting the drive?

ARRRGGGGG!!!!

i have used linux before....as i said i have the newest copy of knoppix, and have had older versions before.... the older version didnt auto mount my ntfs and as i seem to recall mounting it was easier that this..... although i have used linux  before i still consider myself a newb cuz i dont know squat.... im trying to learn and not get discouraged as i have in the past...... 

also as a side note....my linux box isnt able to get online... i only have a wireless and am having trouble with my usb adapter to work at the moment ......

---

### Post by anaconda on 2007-01-25
It should work!
How about trying it without all the "extra" options.

eg.
sudo mount -t auto /dev/hdb1 /media/windows

Then you might need root rights to access it
eg. 
sudo nautilus
or
sudo su

you had the target as:
/media/windows/ 
dont know if it matters, but I newer put the last "/" in that.. shouldn't matter...

---

### Post by crunchyfox on 2007-01-25
alright i guessit was easier than i though i ran that command ... it said the drive was already mounted and busy..... so i sudo su and sudo nautilus... sweet got access to my other drive.... which has my USB wireless adapter drivers on it... woo hoo !!! now will i have to have to run the sudo su and sudo nautilus commands every  time i want to access the drive(if i reboot)? or can it be mounted so that i can read/write to the drive....(ah i know it can, how) 



thanks a bunch

---

