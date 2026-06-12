---
title: "Mounting Partition Problems"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-08-18
Hello everyone,

So i have been through this process before with drapper but recently reformatted all my hard drives and reorganized all my data.  I am now running **7.04**

I have one partition that I would like to use to share files between linux and xp.  I need the partition to mount at start up and i need read/write capabilities.  

Here is an outline of my HD setup.  

**/dev/sda **- This is a 40 gig with NTFS for running windows only.

**/dev/sdb ** - This is a 250 gig hard drive with three separate partitions.  
/dev/sdb1 - Is the file system for ubuntu - 20 gigs
/dev/sdb2 - Is Linux swap space - 1 gig
/dev/sdb3 - Is an ext3 partition that is used to read/write files in ubuntu and xp 100 gigs

I created the folder /mnt/winlinux as a mount point for /dev/sdb3.  Here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=fd165a7c-b812-443e-bdb5-4e67bc6702d7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3464BD0B64BCD13A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=47f814d5-594f-4027-85c5-9329b5214633 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sdb3
/dev/sdb3 /mnt/winlinux ext3 auto,users,rw, 0 2
```

Through Places -> computer i do not see /dev/sdb3 at all.   What went wrong?

---

### Post by randomnote1 on 2007-08-18
I would try something like this

/dev/sdb3  /mnt/winlinux ext3    defaults,errors=remount-ro  0   1

the other thing to check is make sure that the directory /mnt/winlinux exists.

---

### Post by Diabolis on 2007-08-18
Make sure that the UUID is correct. You can check it by typing this:
```
blkid
```

Creat the mount point:
```
sudo mkdir /media/winlinux
```

Mount your partition like this:
```
mount /dev/sdb3 /media/winlinux
```

---

### Post by dreadh3ad on 2007-08-18
I did not include the UUID name.  I used /dev/sdb3 instead.  I thought the two were interchangeable?  

```

baka@baka-linux:~$ sudo mount -t ext3 /dev/sdb3 /mnt/winlinux 
Password:
mount: /dev/sdb3 already mounted or /mnt/winlinux busy
mount: according to mtab, /dev/sdb3 is already mounted on /mnt/winlinux

```

What does /dev/sdb3 /mnt/winlinux ext3 **defaults,errors=remount-ro **0 do?

---

### Post by dreadh3ad on 2007-08-18
I have tried:

/dev/sdb3 /mnt/winlinux ext3 auto,users,rw, 0 2

/dev/sdb3 /mnt/winlinux ext3 defaults,errors=remount-ro 0 

UUID=3d7469e9-2f02-44be-9dfa-bd92bd1e9546 /mnt/winlinux ext3 defaults,errors=remount-ro 0 

none of which work.

The mount point /mnt/winlinux does exist...

---

### Post by dreadh3ad on 2007-08-18
bump because i am stuck :(

---

### Post by dreadh3ad on 2007-08-18
I am still stuck.  What am i doing wrong?  Can anyone shed some light?

---

### Post by Diabolis on 2007-08-18
I know that "mnt" is the folder where mount points are suppoesed to be, but ubuntu also has the "media" folder. If you want to have partition icons over your desktop and menus "media" is where you want to make your mount points. Using paths in your fstab file should be equivalent to using UUID,  but for some reason it won't work (at least in my computer).

> # /dev/sdb3
/dev/sdb3 /mnt/winlinux ext3 auto,users,rw, 0 2

Instead look for the UUID number with blkid and paste it in you fstab file, so your mount point should be somehting like this:
```
UUID=09b049f5-e420-4992-8a19-d784fc40c284 /media/winlinux ext3 defaults 0 2
```

Make the mount point in the media folder with this command:
```
sudo mkdir /media/winlinux
```

And then mount the partition by typing this in the terminal:
```
mount /dev/sdb3 /media/winlinux
```

The icons might not show up at first(I don't know why), but the partition is mounted. You can go and see that all the files of your partition are under the folder /media/winlinux. After I rebooted my laptop the icons appeared. I know it works because I just bought and external hdd yestreday  and I had the same problem this morning.

*bumping is not going to solve your problem

---

