---
title: "How do I read/write to HFS+ disks?"
date: 2006-08-19
forum: Apple PPC Users
---

### Post by Tofu on 2006-08-19
I've got Ubuntu on one hard drive, and Mac OS X on another hard drive (HFS+) on the same machine.

Is there an easy way to transfer files between the two drives?

I'm not used to using command lines, but will do it if there's no other way. I was hoping there might be a way to do it with the GUI.

Do I need extra software to do this?

---

### Post by ssam on 2006-08-19
you do not need any more software, i think you will need to use the command line a bit.

as a preperation step you will need to turn journalling off in mac os x's disk utility.

then have a look at the manualally mounting partitions section of [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) .

the steps are to locate the device name of the hfsplus partition. make a mount mount (a folder which the partition is accessable by). then to modify the file system table ("fstab").

if you have trouble with any of the step feel free to ask.

---

### Post by Tofu on 2006-08-20
Thanks for your reply, Sam.

I ran the script from that help page you linked to.

```
me@Ubuntu:~$ cd
me@Ubuntu:~$ wget http://www.ubuntulinux.nl/files/diskmounter
--08:10:27--  http://www.ubuntulinux.nl/files/diskmounter
           => `diskmounter'
Resolving www.ubuntulinux.nl... 87.250.150.84
Connecting to www.ubuntulinux.nl|87.250.150.84|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,864 (4.8K) [text/plain]

100%[====================================>] 4,864         14.82K/s

08:10:29 (14.80 KB/s) - `diskmounter' saved [4864/4864]
me@Ubuntu:~$ sudo bash diskmounter
Password:
By default the disks will be writable only by root and
Me (me)
Do you want to make the disk writable by all users instead? (y/n)
y
As of Ubuntu 6.04 (Dapper Drake) there is slightly more NTFS writing support
through a very experimental NTFS FUSE module. Using this seems to work but
is NOT recommended. Do you want to use this? [no] no
Not enabling experimental NTFS write support
Added /dev/hda10 as '/media/hda10'
Added /dev/hda12 as '/media/hda12'
Added /dev/hda14 as '/media/hda14'
mount: wrong fs type, bad option, bad superblock on /dev/hda10,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda12,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda14,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

All windows and mac partitions will now be mounted every time you boot
You do not need to reboot, the partitions are mounted now too

```

Still can't see the other Mac drive. The other drive has multiple partitions. Only the OS X start-up drive would be journaled, so I would have thought the other ones would be visiable.

Linux is still a bit hard for the novice user.  :-?

---

### Post by 3rdalbum on 2006-08-21
Go to the command-line and type:

```
gksudo gedit /etc/fstab
```

And check that /dev/hda10, /dev/hda12, and /dev/hda14 have "hfsplus" under the Type column. If not, make the necessary modifications. Then do "pmount -a".

---

### Post by stmiller on 2006-08-21
The HFS+ volume must have journaling turned off, in OS X to be writable, as the other person said.

Then just make a mount point, and mount it.

$ sudo bash
enter your password

$ mkdir /mnt/osx
(or whatever you want to call it)

$ mount -t hfsplus /dev/hda5 /mnt/osx
(or whatever /dev/hda__ your drive is)

---

### Post by Tofu on 2006-08-21
I followed Apple Support Document [107249]("http://docs.info.apple.com/article.html?artnum=107249") and switched off journaling on the OS X side.


In Ubuntu, I launched the Terminal, then typed in:
gksudo gedit /etc/fstab
and got this result...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by winmac_fstab utility
/dev/hda10 /media/hda10 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/hda12 /media/hda12 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/hda14 /media/hda14 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0

```


So, in Ubuntu, I then went searching for the Mac hard drive to see if I could read it. I went to **Places --> Computer ** and clicked on the hard drive icons, but an error message says that the drive cannot be mounted, and may be in the wrong format.

I go to **Places --> Computer --> Filesystem --> Media**, and there are hard drive icons there, but it says they have no items inside  (see image)


Now I try stmiller's method.

Here's my results in Terminal:
```
root@Ubuntu:~# mount -t hfsplus /dev/hda5 /mnt/osx
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Ubuntu:~# mount -t hfsplus /dev/hda10 /mnt/osx
root@Ubuntu:~# mount -t hfsplus /dev/hda12 /mnt/osx
root@Ubuntu:~# mount -t hfsplus /dev/hda14 /mnt/osx

```

Hey, it works! Those last 3 commands did it. I can now find the volumes in
**Places --> Computer --> File System --> mnt --> osx**

Thank you stmiller and everyone who helped.

I hope this thread might help someone else in the future who is searching the same problem.  :-D

---

### Post by stmiller on 2006-08-22
Yes reading/writing support is in the kernel. You don't need some kind of weird script or program.

And yes you have to use YOUR particular /dev/hdaNUMBER

I put /dev/hda5 out as an example. You should just have to mount one thing.
I doubt you have 10, 12, 14 partitions on your system.  And all those lines you made concerning /dev/hda10, 12, 14, etc. in your fstab are confusing and not really needed. I would remove all of those lines.

(Note: to get a root window, just type: sudo bash 
in a command prompt. Mounting must be done as root.)

Do:

$ fdisk /dev/hda

Then press 

p

Now that will show you what place your os x partition is on your hard drive. Whatever is to the left of "Apple_HFS disk1s3 " is your OS X parition. Mount that /dev/hda___ 

(Note: for SATA drives, it will be /dev/sda)

Here is the output of fdisk for my iBook:
```
stmiller@mahler:~$ sudo bash
Password:
root@mahler:~# fdisk /dev/hda
/dev/hda
Command (? for help): p
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2               Apple_HFS disk1s3            166511181 @ 28860387  ( 79.4G)  HFS
/dev/hda3         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hda4         Apple_UNIX_SVR2 untitled            27609376 @ 2018      ( 13.2G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                 1248993 @ 27611394  (609.9M)  Linux swap

Block size=512, Number of Blocks=195371568
DeviceType=0x0, DeviceId=0x0

Command (? for help):

```


(Type q and hit enter to exit fdisk)

FWIW, here is my fstab:

```
root@mahler:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@mahler:~#

```

Don't need any mention of other drives to be able to mount them. On my iBook, I just do this one line:

$ root@mahler:~# mount -t hfsplus /dev/hda2 /mnt/osx

and it is mounted. Note: to unmount, simply type:

$ umount /mnt/osx

For more info:
$ man mount

:)

---

### Post by Tofu on 2006-08-22
Thank you, stmiller, for all that helpful information.

I will keep referring back to this thread, so I can copy and paste your scripts.  :)

---

### Post by jave on 2006-09-16
Just to add to this... WHY does one have to turn off journaling???

---

### Post by jave on 2006-09-16
And in reverse... How do you mount a ext2/ext3 partition under OS X?  Is it possible? :-k

---

### Post by morikaweb on 2006-09-29
I can see how to mount a hfs and hfsplus partition but how do you create one?

Using part or gpart does nto give the options of a hfs or hfsplus partition.

thanks all

---

### Post by Tofu on 2006-10-02
> **morikaweb said:**
> I can see how to mount a hfs and hfsplus partition but how do you create one?

Using part or gpart does nto give the options of a hfs or hfsplus partition.

thanks all
HFS+ is the standard Mac OS file format. My HFS+ partitions were created by Mac OS X when I installed it.

Don't you have Mac OS X operating? It can create HFS+ partitions.

---

### Post by davim on 2008-02-06
[http://partedmagic.com/index.html](http://partedmagic.com/index.html) is able to create hfs+ partitions, Ubuntu should also be able to do this....

Ubunttu should also be albe to write to journalled hfs+ partitions :(

---

