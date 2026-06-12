---
title: "hdb1 permissions problem :("
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by mr.z on 2008-02-16
After geting sick with filled hdds all the time i've gona and got another hdd today.. reformated and got it to auto mount (ext3)

but the permissions aren't right.. i've got it to mount in /filesystem/storeage by following a tutorial but it still shows up as only 1.2 gig free (its a 40 gig drive, my main hdd has only 1.3 gig free)

sooo.. i'm thinking i'll format it yet again, but where should i start? how to get it to mount automaticaly and how to get it with permissions for all users?

also.. whenever i try to sign in as root through the main login its not recognizing any password? is it not possible to login as root? i'm guessing it needs to be in caps i.e. ROOT but thats as far as i can get :/

Thanks for reading

---

### Post by monktbd on 2008-02-16
first of all in ubuntu there is no root account per default lokk [here](https://help.ubuntu.com/community/RootSudo) for some details on that.
generally you need to prepend a command with sudo for a user that has administrative rights to execute a command as root. the first created user automatically has administrative rights. 

regarding your problem:
please post the output of 
```

sudo fdisk -l

```
and 
```

cat /etc/fstab

```

this makes it easier to give you the correct steps and commands and to not corrupt your system.

---

### Post by mr.z on 2008-02-16
```

Disk /dev/hda: 8447 MB, 8447459328 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x051c051c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         977     7847721   83  Linux
/dev/hda2             978        1027      401625    5  Extended
/dev/hda5             978        1027      401593+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c592

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081   83  Linux

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                      0  0  
# /dev/hda1
UUID=ebf11c57-3c84-4529-acf8-ce4ceb4eea64  /               ext3         defaults,errors=remount-ro    0  1  
# /dev/hda5
UUID=40a7f5a7-64d8-4234-b785-871062eac994  none            swap         sw                            0  0  
/dev/hdd                                   /media/cdrom0   udf,iso9660  user,noauto,exec              0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec           0  0  
/dev/hdb1                                  /media/hdb1     ext3         defaults                      0  0  

```

Here ye go..
Ah that explains that! I'd tried redhat ages ago and remembered that haveing a root account so assumed this would also.. 
the sudo thing also, ahh i've copyed and pasted it a few times while working through unrelated minor niggles but now that has actual significance! much appreciated (i did wonder what that was all about!)

---

### Post by monktbd on 2008-02-16
The only thing that probably went wrong was the point of where to mount the new hard disk.

```

/dev/hdb1                                  /media/hdb1     ext3         defaults  

```
in your fstab says that the device hdb1 is mounted to /media/hdb1.
if you look in there you should find your new harddisk in all its glory.
you can always check on the console with the command
```
df
```
how much space is still free on each partition.

the 1.2GB you see free in /filesystem/storeage is very likely the space left on that partition in your old harddisk (/dev/hda1).

you can keep your new harddisk in /media/hdb1.
about the permissions:
first check if you cannot access it as it is right now.
otherwise you would have some options, like making it accessible to everyone (i.e. every user on your computer) or make it owned my you (your user).
just post a 
```

ls -l /media

```
here.

---

