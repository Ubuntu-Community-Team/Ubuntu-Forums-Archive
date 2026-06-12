---
title: "how to mount winXp"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by binary_dream on 2006-11-03
Hi folks, 

I very new in Linux, actually I just installed ubuntu :D though installation went fine with my notebook - HP.

I need now to mount windows (I have to partitions one for winXP and one for ubuntu), but I wanna be able to see files on windows side, so I learned that I have to mount windows and I tried this:
> 
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222


but I get this error:
> 
Wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
....
..


What do I have to do in order to mount it? that way obviously is not working :(

Another question is how do I know if all the drivers were installed correctly in my notebook? I hear a lot of people talking about yast do we have yast in ubuntu ?


Thanx a lot, and pardon my ignorance

---

### Post by mark_g on 2006-11-03
Most likely your Windows partition isn't hda1, so try using hda2, hda3 (or maybe hdb1 if you have multiple hard drives, but probably not, because it's a laptop).

YaST is SuSE's "Yet Another Setup Tool" used to configure your system. Ubuntu doesn't have that. It has other tools which are just as good to configure your system.

To check if all your drivers are installed, I think you should only check your video card driver. You might want to install a different one if you have an Nvidia or ATI card. Sound and stuff will most likely work just out of the box.

Let me know if you need more info.

---

### Post by Herman on 2006-11-03
I agree with mark_g,
It looks like your commands are okay. you have an extra slash after /windows there, in your mount command, but I don't think that would matter. That should work if the partition number is correct. Also, possibly look at whether it should be 'sda1' instead of 'hda1' maybe?
An easy way to confirm your partition numbers would be to use the command 'sudo fdisk -lu', or check with disk partitioning software.
```
sudo fdisk -lu
```Regards, Herman :D

---

### Post by Archmage on 2006-11-03
There is a possibility that your Windows partition is already mounted. I think the last time I did install Edgy it did mount it on /home/windows.

Please perform the command *mount* and see if the partition is already there.

---

### Post by Herman on 2006-11-03
>                               Wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
....
.. Hmmm, not to mention the obvious, is this filesystems actaully NTFS as we are all presuming, or might it be something else as the error message is trying to tell us?  :-k

If the filesystem is FAT32, which is, by the way, a better filesystem for dualbooting with, your mounting command would look more like this one,```
sudo mount /dev/hda1 /media/windows -t vfat -o umask=000
``` Regards, Herman :D

Edit: Archmage is correct too, it should already be mounted automatically in Edgy. I have noticed that this does not happen in all installs automatically though, I don't know why not.

---

### Post by binary_dream on 2006-11-03
> **Herman said:**
> 
If the filesystem is FAT32, which is, by the way, a better filesystem for dualbooting with, your mounting command would look more like this one,```
sudo mount /dev/hda1 /media/windows -t vfat -o umask=000
``` Regards, Herman :D


I tried that too but I got the same error.

By the way there is nothing in my home folder, no windows :(

---

### Post by bodhi.zazen on 2006-11-03
output of:```
sudo fdisk -l && cat /etc/fstab
```

---

### Post by binary_dream on 2006-11-03
okay I solved the problem, I dont know really how, but all I did I restarted the pc and then entered the same command on terminal and worked :KS 

thanks for help and your time

---

