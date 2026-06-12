---
title: "How to save and delete files from a 2nd hard drive"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by 123james on 2007-05-23
Hi everyone,

GREAT forum!

I'm brand new to Linux - installed Ubunto for the first time today and love it!  I have a PC with two physical hard drives (as opposed to a single drive with a partition).

The problem I have is that** I would like to save files to the second hard drive - but am not allowed to because it is owned by 'root'.  I know how to get the terminal window up but have no idea how to change the permissions, so I can actually store data on that 2nd drive.**

ANY help would be really appreciated guys!

**The drive is working and it is definitely a second hard drive and not a partition.**


Many, many thanks!

James
[COLOR="Red"]**PS - Thank all of you who have answered other people's problems, as this has been INVALUABLE to me today!**[/COLOR] :)

---

### Post by taurus on 2007-05-23
What is the filesystem of that second harddrive and where do you mount it?  Post the output of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by bobplano on 2007-05-23
try something like this

sudo chown -R $USER:$USER /wherever/it/is

change the info to fit for you

---

### Post by 123james on 2007-05-23
> **taurus said:**
> What is the filesystem of that second harddrive and where do you mount it?  Post the output of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```
Thanks Taurus and Bobplano,

The file system is the same on both hard drives - being as I can save and delete from the first hard drive I assume the file system on the second drive is ok.

I am not 100% what 'mounted' means - but the 2nd drive appears as an icon on my desktop - so I think it's mounted there - if that sounds crazy, im new to this guys!!

Hope this helps?


James
Thanks for your help!

---

### Post by taurus on 2007-05-23
We can figure this one out real quick if you just run those three little commands from a terminal, Applications -> Accessories -> Terminal, and post the outputs here.

---

### Post by 123james on 2007-05-23
Hi Guys,

Here's what I got when I entered those three lines:

**FIRST:**
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Extended
/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris


**SECOND:**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d45235e4-6830-4105-9942-f7888611471d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=b044cf85-e7fe-4efd-9a6a-9a88c2277fc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

**AND THIRD:**
Filesystem            Size Used Avail Use% Mounted on
/dev/sdb1              71G  2.1G   65G   4% /
varrun                506M  232K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  116K  506M   1% /proc/bus/usb
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              71G  2.0G   65G   3% /media/disk



Thanks for your help!!


James

---

### Post by aks44 on 2007-05-23
I had the very same problem with my second hard drive, and solved it by adding
```
uid=1000,gid=1000
```to the options of the relevant /etc/fstab line.

In my case the relevant line looks like :
```
/dev/sdb1 /home/ysma/data ntfs auto,uid=1000,gid=1000,ro,user,nls=utf8 0 0
```

I guess 1000 is the default user's identifier on all newly installed (K)Ubuntu's, but YMMV (I'm too much of a Linux/Ubuntu newb to be certain of that). That's worth a try anyway, as it can hardly damage the data on the second drive (at worst, you'll still get an "access denied" error).

If the partition is already mounted when you edit /etc/fstab you will have to unmount/remount it.

**Edit:**
[QUOTE="bobplano"]sudo chown -R $USER:$USER /wherever/it/is[/QUOTE]As far as I am concerned, I tried that and this didn't solve anything.

---

### Post by 123james on 2007-05-23
[QUOTE=aks44;2708642]I had the very same problem with my second hard drive, and solved it by adding
```
uid=1000,gid=1000
```to the options of the relevant /etc/fstab line.

In my case the relevant line looks like :
```
/dev/sdb1 /home/ysma/data ntfs auto,uid=1000,gid=1000,ro,user,nls=utf8 0 0
```

Thanks.  As someone that installed Ubuntu for the first time earlier today, I have NO IDEA how to enter that code you kindly suggested.

I know how to open the terminal window - what do I do after that in order to do as you suggested and 'add' that code?

Thanks guys.


James

---

### Post by 123james on 2007-05-23
> **123james said:**
> Hi Guys,

Here's what I got when I entered those three lines:

**FIRST:**
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Extended
/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris


**SECOND:**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d45235e4-6830-4105-9942-f7888611471d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=b044cf85-e7fe-4efd-9a6a-9a88c2277fc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

**AND THIRD:**
Filesystem            Size Used Avail Use% Mounted on
/dev/sdb1              71G  2.1G   65G   4% /
varrun                506M  232K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  116K  506M   1% /proc/bus/usb
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              71G  2.0G   65G   3% /media/disk



Thanks for your help!!


James

[COLOR="Navy"][B]Was that information enough for you to go on?


Thanks guys,

James[/B][/COLOR]

---

### Post by aks44 on 2007-05-23
hmm it's strange you don't already have a /dev/sda1 line in /etc/fstab...

try (for ubuntu)
```
sudo gedit /etc/fstab
```
or (for kubuntu)
```
sudo kate /etc/fstab
```

and add this line to the file (or modify the existing /dev/sda1 line) :
```
/dev/sda1 /media/disk ext3 noauto,user,ro,uid=1000,gid=1000 0 0
```

then check that an *empty* directory /media/disk exists. create it if necessary using
```
sudo mkdir /media/disk
```

then
```
umount /media/disk         [NOTE you may get an error message with this first one but just ignore it]
mount /media/disk
```

if you can access the disk drive (which I put in read only mode, for safety), edit /etc/fstab again and change "ro" with "rw" to allow write access, and "noauto" with "auto" to have it mounted automatically when you boot your machine.

let us know if this helps !

---

### Post by 123james on 2007-05-23
> **aks44 said:**
> then check that an *empty* directory /media/disk exists. create it if necessary using
```
sudo mkdir /media/disk
```

if you can access the disk drive (which I put in read only mode, for safety), edit /etc/fstab again and change "ro" with "rw" to allow write access, and "noauto" with "auto" to have it mounted automatically when you boot your machine.

let us know if this helps !




ASK44,
i am going through what you have just said - stuck here.  How do i know if an empty directory/media exists - I have been using Linux for just 5 hours so please make it as simple as possible.

Thanks for your help!!!


James

---

### Post by aks44 on 2007-05-23
try
```
ls /media/disk
```

you may have three kinds of output :
- "no such file or directory" :```
sudo mkdir /media/disk
```
- "access denied" : ```
umount /media/disk          [NOTE that shouldn't give an error back]
[OR]
sudo umount /media/disk            [if the above umount said you must be root]
```
- an empty answer => all is fine

then follow the rest of the instructions

now I'm sorry, it's 00:30 here so I'm gonna sleep now if I want to be able to go to work tomorrow ;)

I hope that solves your problem, anyway I'll check tomorrow after work to see if all went fine.

---

### Post by eoghanmurray on 2007-05-26
I have two extra hard drives, one, which is solely for Windows XP (internal), and  an extra partition on my USB HDD, which has Ubuntu installed on.

Windows Internal drive: NTFS
Windows External Partition: NTFS
Linux External Partition: EXT3

Both the NTFS drives are set to access-files only, and I can't write to them. Any ways around this?
I'm only new in Ubuntu, so simplish English please.

---

### Post by aks44 on 2007-05-26
> **eoghanmurray said:**
> Both the NTFS drives are set to access-files only, and I can't write to them. Any ways around this?
I know there are ways to write to an NTFS partition (I don't know how, however), but AFAIK you risk breaking it. That's why NTFS partitions are read-only by default.

---

### Post by bobplano on 2007-05-27
you need something called ntfs3g. it allows you to write to ntfs. if you are using fiesty you should be able to just search for it in synaptic. also get ntfs-config for a graphical frontend

---

