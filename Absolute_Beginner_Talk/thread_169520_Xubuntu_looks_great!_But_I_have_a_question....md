---
title: "Xubuntu looks great! But I have a question..."
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-02
I just installed Xubuntu on my computer with 2 harddrives. I only formatted the master hard drive for linux (removed windows 98 completely). Now, I want to format the other hard drive to linux. However, I have no idea where any of my drives are. I think "File System" is my master hard drive. That is the only one that shows up. How can I find all the hard drives connected to my system?

Thanks!

---

### Post by nanotube on 2006-05-02
don't know about xubuntu utilities, but there must be a disk administration tool somewhere ...

to change partitions and format stuff, probably best to use "gparted" partition editor. install it with "sudo apt-get install gparted".

---

### Post by nalmeth on 2006-05-02
I know that dapper has a devices manager that you can throw on the panel, but I think this is a new tool. Nonetheless you should try to add items to the panel, and look for that.
Sound like what you're looking for.
In the command line take a look with this command
cat /etc/fstab
see if your extra drive's there
Gparted of course can do the partitioning

---

### Post by Belathor on 2006-05-02
The hard drive is definitely installed. gparted found it and I formatted it to ext3. (Should I change that? Should the second hard drive be ext2?) However, I still have no idea how to access it. Thunar (XFCE file manager) only shows my user name and "file system".

Thanks for the help!

---

### Post by nanotube on 2006-05-02
[QUOTE=Belathor]The hard drive is definitely installed. gparted found it and I formatted it to ext3. (Should I change that? Should the second hard drive be ext2?) However, I still have no idea how to access it. Thunar (XFCE file manager) only shows my user name and "file system".

Thanks for the help![/QUOTE]
to see what you have mounted to the filesystem, and to where, open a terminal and run command "df".
see if your drive is mounted anywhere. if not, you will have to add an entry to /etc/fstab - just post here, and someone will tell you what to add. :)

oh, and btw, ext3 is just fine to use as a filesystem.

---

### Post by Belathor on 2006-05-03
ok, so it's not mounted to the filesystem. That makes sense.

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18793496   1536940  16301896   9% /
varrun                  257872        80    257792   1% /var/run
varlock                 257872         4    257868   1% /var/lock
udev                    257872       128    257744   1% /dev
devshm                  257872         0    257872   0% /dev/shm
lrm                     257872     18744    239128   8% /lib/modules/2.6.15-21-386/volatile

I believe that the second hard drive is called hdb or something like that. So, how do I add an entry to /etc/fstab? What do I add?

Thanks!

---

### Post by Belathor on 2006-05-03
Yep, its /dev/hdb (the hard drive I want to add to the file system).

---

### Post by nanotube on 2006-05-03
well, run
sudo fdisk -l /dev/hdb
to see what partitions you have on your hdb
say, for example, that it is hdb1. 
then in your fstab add
```
/dev/hdb1       /data               ext3    defaults,errors=remount-ro 0       0
```
(replace /data with whatever directory you want to mount it to - and then make sure to actually create that directory with "sudo mkdir -p /bla/bla")
and then run 
```
sudo mount /data
```

---

### Post by Belathor on 2006-05-03
[QUOTE=nanotube]well, run
sudo fdisk -l /dev/hdb
to see what partitions you have on your hdb
say, for example, that it is hdb1. 
then in your fstab add
```
/dev/hdb1       /data               ext3    defaults,errors=remount-ro 0       0
```
(replace /data with whatever directory you want to mount it to - and then make sure to actually create that directory with "sudo mkdir -p /bla/bla")
and then run 
```
sudo mount /data
```[/QUOTE]

What is my fstab? :confused:

---

### Post by Belathor on 2006-05-03
file system tab through the file manager?

---

### Post by Belathor on 2006-05-03
Ok. That was a dumb question. Wikipedia took care of that. So ds is the command for accessing the file system table, right? And then, how do I add things?

Thanks!

---

### Post by Belathor on 2006-05-03
```
Disk /dev/hdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2491    20008926   83  Linux
```

That is all there is on the other hard drive.

---

### Post by Belathor on 2006-05-03
Ok. I have no idea how to use the command line! I have no idea how to create directories! Are there any howtos and tutorials you would recommend that would help figure this out for myself?

Thanks!

---

### Post by nanotube on 2006-05-03
ok, so there is just one partition, /dev/hdb1, that's cool. 
so edit the /etc/fstab like i said before.

yes, you definitely want to figure out how to navigate the command line. go to the first link in my sig (the customization howto), and there find the section "other command line resources". you will see a list of nice commandline tutorials - give them a look. :)

in this particular case, to edit your fstab, here is what you do. open a terminal (Applications>Accessories>Terminal), and enter the following command:
```
sudo nano /etc/fstab
```
once you are there, scroll to the end, and paste in the line that i said to add, before:
```
/dev/hdb1       /data               ext3    defaults,errors=remount-ro 0       0
```
now hit control-x, and the enter key - this will save the file.
now, run this command:
```
sudo mkdir /data
```
this will make the /data directory where we are mounting your drive.
and now run 
```
sudo mount /data
```
and you should have your drive mounted (and it will mount automatically on reboot from now on).
to make sure it is mounted, run command "df" and see for yourself. :)

---

### Post by Belathor on 2006-05-03
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18793496   1546460  16292376   9% /
varrun                  257872        80    257792   1% /var/run
varlock                 257872         4    257868   1% /var/lock
udev                    257872       124    257748   1% /dev
devshm                  257872         0    257872   0% /dev/shm
lrm                     257872     18744    239128   8% /lib/modules/2.6.15-21-386/volatile
/dev/hdb1             19694836    131228  18563164   1% /storage
```

Yay! So the hard drive mounted. I looked in the file manager and it is there! Thanks, nanotube!:D

---

### Post by nanotube on 2006-05-03
excellent! you're welcome. have fun with all that free disk space you have :)

---

