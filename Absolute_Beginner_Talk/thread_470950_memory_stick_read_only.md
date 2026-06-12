---
title: "memory stick read only??"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-06-11
hi
im planing to reinstall linux(the updates screwed stuff up) and i wanna back up data to a memory stick pro card. the problem is that even though the computer detects it and mounts it, i cant write to it, or delete from it
is there a terminal comand i can use to overwrite it or format it so i can use it?

---

### Post by edwardLS on 2007-06-11
I certainly am not an expert in this area, but it sounds similar to a problem I had at one time.  Is it possible that the memory stick is mounted as "root" owned.  If that is the case you need to mount it as the user that wants to use it, or use 'sudo' with what ever backup you are doing.

Hope this helps.

---

### Post by Inxsible on 2007-06-11
Its probably a permissions issue. You can assume ownership by
```
sudo chown -R <your username>:<your group> <device mount path>
```

---

### Post by 99bluefoxx on 2007-06-11
ok thanks
gonna try that

---

### Post by Inxsible on 2007-06-11
> **99bluefoxx said:**
> ok thanks
gonna try that
Hope it helps !
 
Post back your fdisk -l , if you have any problems

---

### Post by p_quarles on 2007-06-11
I had a similar problem with every USB stick drive I've used with Ubuntu. My workaround was just to format it as a FAT32 and they all worked fine after that.

---

### Post by Inxsible on 2007-06-11
> **p_quarles said:**
> I had a similar problem with every USB stick drive I've used with Ubuntu. My workaround was just to format it as a FAT32 and they all worked fine after that.
Did you ever try changing permissions on the mount point ?
 
I have never had a problem after I change permissions.

---

### Post by p_quarles on 2007-06-11
> **Inxsible said:**
> Did you ever try changing permissions on the mount point ?
 
I have never had a problem after I change permissions.
No, I didn't, but I'll give that a try the next time. Frankly, though, I think the problem is that a lot of those things come preinstalled with stuff to work with Win and OS X. My Kingston 2GB, for instance, looked blank under Windows, but showed a bunch of files with strange characters when I loaded it into linux.

---

### Post by 99bluefoxx on 2007-06-11
> **Inxsible said:**
> Its probably a permissions issue. You can assume ownership by
```
sudo chown -R <your username>:<your group> <device mount path>
```
ok tried it but it still is read only
now what?

---

### Post by Inxsible on 2007-06-11
> **p_quarles said:**
> No, I didn't, but I'll give that a try the next time. Frankly, though, I think the problem is that a lot of those things come preinstalled with stuff to work with Win and OS X. My Kingston 2GB, for instance, looked blank under Windows, but showed a bunch of files with strange characters when I loaded it into linux.
 
That could be a problem, yes !!

---

### Post by Inxsible on 2007-06-11
> **99bluefoxx said:**
> ok tried it but it still is read only
now what?
Post the output of ```
sudo fdisk -l
``` -l is lowercase L. Make sure your disk is connected when you do this.

---

### Post by Campingman on 2007-06-11
To get around the same problem I had with an SD card.  I formatted it to FAT32 in Ubuntu (Gparted).  I had previously tried it in Windows and it remained read only in Ubuntu.  It was very odd but after format with Gparted It mounted with full permissions and has been moderately OK since.

---

### Post by 99bluefoxx on 2007-06-11
> **Inxsible said:**
> Post the output of ```
sudo fdisk-l
``` -l is lowercase L. Make sure your disk is connected when you do this.
sudo: fdisk-l: command not found
is what it tells me

---

### Post by p_quarles on 2007-06-11
I think there's supposed to be a space between fdisk and -l 

Try that.

---

### Post by Inxsible on 2007-06-11
> **p_quarles said:**
> I think there's supposed to be a space between fdisk and -l 
 
Try that.
p_ quarles is right. I am sorry, I typed too fast and didnt realize i missed the space. I will correct it in my earlier post too.

---

### Post by 99bluefoxx on 2007-06-11
> **p_quarles said:**
> I think there's supposed to be a space between fdisk and -l 

Try that.
ok got it

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/sda: 14 MB, 14909440 bytes
2 heads, 32 sectors/track, 455 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         455       14531+   1  FAT12

Disk /dev/sdd: 504 MB, 504365056 bytes
32 heads, 32 sectors/track, 962 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         961      491789+   7  HPFS/NTFS

Disk /dev/sde: 517 MB, 517472256 bytes
256 heads, 47 sectors/track, 84 cylinders
Units = cylinders of 12032 * 512 = 6160384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          84      505320+   b  W95 FAT32
```

---

### Post by Inxsible on 2007-06-11
Ok which drive are you trying to get permission on?
14MB -- sda ?
504MB -- sdd ?
or 517MB -- sde ?

---

### Post by 99bluefoxx on 2007-06-11
> **Inxsible said:**
> Ok which drive are you trying to get permission on?
14MB -- sda ?
504MB -- sdd ?
or 517MB -- sde ?
sdd and sda, sde is my mp3 player

---

### Post by Inxsible on 2007-06-11
> **99bluefoxx said:**
> sdd and sda, sde is my mp3 player
Assuming that they are mounted in /media/sda1 and /media/sdd1, and assuming your username and group to be bluefoxx
```
sudo chown -R bluefoxx:bluefoxx /media/sda1
```
```
sudo chown -R bluefoxx:bluefoxx /media/sdd1
```

---

### Post by 99bluefoxx on 2007-06-11
> **Inxsible said:**
> Assuming that they are mounted in /media/sda1 and /media/sdd1, and assuming your username and group to be bluefoxx
```
sudo chown -R bluefoxx:bluefoxx /media/sda1
``````
sudo chown -R bluefoxx:bluefoxx /media/sdd1
```
tried it but it says
```

chown: cannot access `/media/sda1': No such file or directory
```
and
```

chown: cannot access `/media/sdd1': No such file or directory

```
when i try either command

---

### Post by Inxsible on 2007-06-11
if the above still doesnt work, you will have to mount them manually
 
```
sudo mount -t vfat /dev/sda1 /media/sda1
```
 
and
 
```
sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1
```

---

### Post by Inxsible on 2007-06-11
> **99bluefoxx said:**
> tried it but it says
```

chown: cannot access `/media/sda1': No such file or directory
```
and
```

chown: cannot access `/media/sdd1': No such file or directory

```
when i try either command
 
I assumed that your drives were mounted at /media/sda1 and /media/sdd1. You need to replace them by your actual mount points. They will probably be under /media itself

---

### Post by 99bluefoxx on 2007-06-11
tried it heres one result

```
bluefoxx@bluefoxx-unix:~$ sudo mount -t vfat /dev/sda1 /media/memory stick drive
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
bluefoxx@bluefoxx-unix:~$ 

```

---

### Post by Inxsible on 2007-06-11
> **99bluefoxx said:**
> tried it heres one result
 
```
bluefoxx@bluefoxx-unix:~$ sudo mount -t vfat /dev/sda1 /media/memory stick drive
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
bluefoxx@bluefoxx-unix:~$ 

```
 
you need to put quotes around /media/memory stick drive...since you are using whitespace in the name. I would refrain from using whitespace at all. Change the name to memorystickdrive

---

### Post by Inxsible on 2007-06-11
Did you first try changing the mount point names? It seems you are trying both solutions simultaneously. You wouldn't know whats what in that case.

---

### Post by 99bluefoxx on 2007-06-11
> **Inxsible said:**
> Did you first try changing the mount point names? It seems you are trying both solutions simultaneously. You wouldn't know whats what in that case.
i tried both seperatly but the output result is pretty much the same
ive gotta get to school now but ill try this when i get back then post again
thanks for all hepl and patience so far anyways

---

### Post by themis on 2007-06-14
Hi to all!
I would like some help too, I have a similar problem.

Here is what is posted when I *sudo fisk -l*
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   7  HPFS/NTFS

```

The only-read disk that I want to change permissions is sdb. 
Thanks for any help!

---

### Post by Inxsible on 2007-06-16
> **themis said:**
> Hi to all!
I would like some help too, I have a similar problem.

Here is what is posted when I *sudo fisk -l*
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   7  HPFS/NTFS

```The only-read disk that I want to change permissions is sdb. 
Thanks for any help!

sdb1 or sdb5 ?

Changing permission can be done like so
```
sudo chmod ugo /dev/sdb1
``` But i think you would have to change the permissions on the mount point rather than the device. Where is sdb1 mounted?
Where is sdb5 mounted ?

---

### Post by porloporlo on 2008-02-07
hello am a newie here and i have a problem
HOW CAN I MAKE THE CONTENT OF MY MEMORY STICKS TO BE READ ONLY FILES ie i dont want them to be copyable

thanks

---

