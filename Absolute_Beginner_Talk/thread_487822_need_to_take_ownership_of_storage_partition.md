---
title: "need to take ownership of storage partition"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Bleak Outlook on 2007-06-29
i have made a storage partition just for files i want to keep like music and films 
thus keeping as much free space on Ubuntu as possible

the problem is although the partition shows up on my desktop
im unable to use it
trying to add anything to it results in this message

> You do not have permissions to write to this folder.

how would i be able to gain permission as it seems strange that its shown but unusable


on a side note 
as you can see i also have a partition for windows storage
imaginatively titled "windows store" ;)
is there anyway i would be able to add files to that from Ubuntu 
i can read from it but im not able to add stuff
i know that its a different file system and expect its not possible
im just curious 

thanks for your time

---

### Post by orb9220 on 2007-06-29
In a term:

**gksudo gedit /etc/fstab**

copy and paste contents here.

---

### Post by Bleak Outlook on 2007-06-29
i hope this is wot you asked for? 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cf2c9141-18fd-41a5-a3ba-dc55accaa646 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=24808A1E8089F718 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=30123BAC123B7646 /media/sda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=6B1EB49CE17F924C /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=c88b1c42-8f36-bd6e-a02c-fd8424916822 /media/sdb6     ext3    defaults        0       2
# /dev/sda2
UUID=586e7975-3e6e-4d7b-887e-98a0d8128134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

im sorry ? it looks really messy 
i hope this helps
i really am just this techno-tarded

---

### Post by Songwind on 2007-06-29
This code will make your user the owner:

```
 sudo chown -R <user name> <storage folder>
```

---

### Post by Bleak Outlook on 2007-06-29
> **Songwind said:**
> This code will make your user the owner:

```
 sudo chown -R <user name> <storage folder>
```


fella your a :KS 

just one more question
is this a permanent change or will i have to do this each time i want to add something or after i reboot or anything along those sorta lines?

         =D>=D>=D>=D>=D>=D>=D>

thanks again fella 
all the best and be lucky

bleak

---

