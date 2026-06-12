---
title: "Getting my ipod to work"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by bamend on 2006-08-22
using the thread [http://www.ubuntuforums.org/showthread.php?t=103071&highlight=itunes](http://www.ubuntuforums.org/showthread.php?t=103071&highlight=itunes)
I made the /mnt/ipod directory. I plugged the ipod in and found out the ipod is recognized as sdb2, I added this line to the /etc/fstab 
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
then I mounted the ipod with: sudo mount /dev/sda2
Now in my media folder I have two subfolders: ipod which is blank and ipod-1 which has all the information from the ipod in it.  Then when I try to access the ipod from amaroK or gtkpod, neither program recognizes the ipod.  What am I doing wrong?  I've messed with this for two complete days and tried several different ways to do this without success.  please help as I'm extremely frustrated.

---

### Post by sonny on 2006-08-22
> **bamend said:**
> I plugged the ipod in and found out the ipod is recognized as sdb2, I added this line to the /etc/fstab 
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
then I mounted the ipod with: sudo mount /dev/sda2
If your ipod is been recognize as sdb2 then you should change your fstab to /dev/sdb2 /mnt/ipod vfat user,noauto,umask=000 0 0 then do sudo mount /dev/sdb2 /mnt/ipod

---

### Post by bamend on 2006-08-22
My mistake.  My fstab file has this in it:
/dev/sdb2 	/mnt/ipod 	vfat user,noauto,umask=000 0 0

and it still doesn't work.

---

