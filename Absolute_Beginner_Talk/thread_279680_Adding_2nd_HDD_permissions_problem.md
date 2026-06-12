---
title: "Adding 2nd HDD permissions problem"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Twig E. Pottox on 2006-10-18
Thought it would be easy after doing this many time with other OS. Newbie Adding a 2nd (new) HDD to Umbuntu 6.10 Gnome box (800Mhz /640MB ram.  did Fdisk, partitioned and formatted and mounted to files.  

Problem is it seems is that the files I have created to mount the new drive to are locked.  therefore when I try to access the new drive partitions I get: "The Folder contents cannot be displayed because I do not have permission to view the contents of (folder name)" 

What's going on? I create a file then the system denies me access to it? I've tried a number of methods from the Umbuntu forums Psycocats etc. to no avail.](*,)  running out of hair to pull out. help!:evil:

---

### Post by CatKiller on 2006-10-18
The permissions of the mount point don't matter - its the permissions used in the mount command that are critical. You say you've read the Psychocats guide - have you read [this one?]("http://ubuntuguide.org/wiki/Dapper")

What are the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by aysiu on 2006-10-18
One of these guides should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Twig E. Pottox on 2006-10-19
> **CatKiller said:**
> The permissions of the mount point don't matter - its the permissions used in the mount command that are critical. You say you've read the Psychocats guide - have you read [this one?]("http://ubuntuguide.org/wiki/Dapper")

What are the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```
Thanks for your advice. I  admit I need to do more preliminary reading on the OSs' fundamentals. I just didn't know that adding a drive would take 12+ hous of head bashing. 

here are the outputs you requested and then some more, note there is a DVD and a CDRW on the system:


steve@bastid:~$ sudo fdisk-l
Password:
sudo: fdisk-l: command not found
steve@bastid:~$ sudo fdisk -l

Disk /dev/hde: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2392    19213708+  83  Linux
/dev/hde2            2393        2498      851445    5  Extended
/dev/hde5            2393        2498      851413+  82  Linux swap / Solaris

Disk /dev/hdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        3000    24097468+  83  Linux
/dev/hdf2            3001        4865    14980612+  83  Linux
steve@bastid:~$



following the guide from Psychocats - "Mounting Linux partitions/Drives in Ubuntu" i got these outputs:

  GNU nano 1.3.10             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdf1       /               ext3    defaults        0       0
/dev/hdf2       /storage        ext3    defaults        0       0


steve@bastid:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdf2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

steve@bastid:~$


steve@bastid:~$ sudo chown-r steve:steve /storage
sudo: chown-r: command not found
steve@bastid:~$ sudo chown -r steve:steve /storage
chown: invalid option -- r
Try `chown --help' for more information.
steve@bastid:~$ chmod -r 755 /storage
chmod: cannot access `755': No such file or directory
chmod: changing permissions of `/storage': Operation not permitted
steve@bastid:~$



Where is sunny southend on sea?

---

### Post by CatKiller on 2006-10-19
You appear to have two partitions mounted at /. That really can't be a good thing. Make a new directory called /storage2 or something and change the hdf1 line so that it's mounted there instead.

Are you sure that the hdf2 partition is ext3?

Syntax is very important when using the command line. You've noticed that you'd missed out the space, but it should be **-R** rather than -r on both the chown and chmod commands.

> Where is sunny southend on sea?

It's more a state of mind, really, since in the real Southend-on-Sea, in Essex - Great Britain - it's pissing down.

---

### Post by Twig E. Pottox on 2006-10-19
> **CatKiller said:**
> You appear to have two partitions mounted at /. That really can't be a good thing. Make a new directory called /storage2 or something and change the hdf1 line so that it's mounted there instead.

Are you sure that the hdf2 partition is ext3?

Syntax is very important when using the command line. You've noticed that you'd missed out the space, but it should be **-R** rather than -r on both the chown and chmod commands.

Thanks again will be trying asd advise of success later - Case sensitivity, lovely. believe it oor not I wasn't bad at the command line with dos back inthe 80's it will come back


It's more a state of mind, really, since in the real Southend-on-Sea, in Essex - Great Britain - it's pissing down.

you threw me with the "sunny" bit. cheers from the suburban paradise of northern Illinois.

---

### Post by aysiu on 2006-10-19
This is weird.

In your /etc/fstab, you have /dev/hde1 mounted at /
You also have /dev/hdf1 mounted at /

Only one partition can be mounted to a particular location. I suspect that /dev/hde1 is the real /
So you have to change that line about /dev/hdf1 to something else.

The weird part is that the error seems to be with /dev/hdf2, not /dev/hdf1. It looks okay, but did you create the storage directory? ```
sudo mkdir /storage
``` before you did ```
sudo mount -a
```?

Also for *chown*, you need a capital *R*: ```
sudo chown -R steve:steve /storage
```

---

### Post by Twig E. Pottox on 2006-10-19
thanks again for the advise and noting case sensitivity.  will be applying your input later and will advise hopefully of success thanks.

---

### Post by Twig E. Pottox on 2006-10-19
Thanks again, i did create the directory before i tried to mount it. will advise of sucess later

---

### Post by Twig E. Pottox on 2006-10-20
I applied changes , ran mount-a and it said it did not recognoze the file systenm on the new drive.  

furhtermore upon re- booting the machine it now "can not start x server due to some internal error".

from the command line now alli have I ran fstab and foted that hde/1 listed as default and hdf/1 and/2 are listed as defaults. I believe this is the only file I could have corrupted.

What gives? shold I re install the system with the 2nd HDD installed? If so how can I save data on hde1 through another install?

---

