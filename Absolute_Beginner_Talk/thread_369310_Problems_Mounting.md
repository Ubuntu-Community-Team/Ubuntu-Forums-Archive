---
title: "Problems Mounting"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by thespeth on 2007-02-24
Hi everyone,

I'm a fairly new Linux user, and after trying a few distros, I think I've settled in with Xubuntu. Only, I'm having a few problems at the moment...

I can't connect with my wireless card. I've seen several guides online on how to fix that. But first, so I can help myself fix the wireless problem, I need to...

Figure out how to mount a partition. I've tried several things, including mount -t vfat /dev/hda4 /mnt but to no avail, and also I tried to load ivman from the disc with sudo apt-get install ivman (linux is installed on my computer and I thought maybe ivman was on the cd?). I got a message informing me that it wasn't there.

The most frustrating thing so far is that the ONLY internet connection I have in the house is wireless (I just moved into this place recently with a friend), so when I want to try and do something in xubuntu, I have to write it down on paper, restart, try it in linux, restart again and then look for something else. Quite frustrating.

So, if anyone could give me a hand, being able to mount a drive would make my life easier because I could at least save a text or something to it and load several ideas for the wireless problem at a time later on in xubuntu (the instructions for the wireless problem were too long to write down).

I thank anyone who would offer help, and I apologize in advance if this is child's play; like I said, I'm pretty wet behind the ears when it comes to this stuff.

I don't know what kind of information I should provide, so please, feel free to administer some tough love :-D

---

### Post by thespeth on 2007-02-24
*bump*

---

### Post by logos34 on 2007-02-24
what's the ouput from 
> sudo fdisk -l
?

Did you create the mount point first?
> sudo mkdir /mnt

/mnt/fat32 or /media/windows would be better

Post your /etc/fstab file too.

---

### Post by thespeth on 2007-02-24
fdisk -l

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hda2            1021        3570    20482875   83  Linux
/dev/hda3            3571        3952     3068415   82  Linux swap / Solaris
/dev/hda4            3953        9729    46403752+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/hdb5               2        9729    78140128+   7  HPFS/NTFS


Ugh, that formatting look awful...

I'm trying to mount hdb, which, actually, I just tried to format because I saw it was ntfs and QTParted wouldn't let me mess with it.

How do I look at /etc/fstab?  I'm getting a permission denied error when I load it in the terminal.

I'm now on the floor in the closet in the basement with the laptop.  The roommate told me that there was no place to hook up a cable to the router that verizon installed, but I guess I shouldn't have taken his word for it.  At least it's easier to retrieve the information from Xubuntu without having to actually write it down with pen and paper.  :D

---

### Post by RedSquirrel on 2007-02-24
Yes, definitely post your /etc/fstab file.

Depending on how things are setup on your system, there might be a line for /dev/hda4 in /etc/fstab. If the line itself is setup correctly, you could just do:

```
mount /dev/hda4
```

or 

```
mount <mount-point>
```

where <mount-point> is whatever mount point is specified for /dev/hda4 in /etc/fstab.

---

### Post by RedSquirrel on 2007-02-24
To access /etc/fstab:

```
gksudo mousepad /etc/fstab
```

or you could do

```
more /etc/fstab
```

select everything with your mouse, and then middle-click to paste into the editor for these forums.

---

### Post by thespeth on 2007-02-24
/etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=75b2bb03-a442-4be7-98c2-69050fdb8d2d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0C3499573499451C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=C8A8510FA850FCFE /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=ce75f940-e8a2-4824-aec8-fe43ea2d46aa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by logos34 on 2007-02-24
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=75b2bb03-a442-4be7-98c2-69050fdb8d2d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=0C3499573499451C /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
[B]# /dev/hdb5
UUID=C8A8510FA850FCFE /media/hdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1[/B]
# /dev/hda3
UUID=ce75f940-e8a2-4824-aec8-fe43ea2d46aa none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

The entry looks correct, but it's NTFS not fat32 (it's inside an extended partition which looks like the one above).  It should have created a mount point hdb5 in /media dir.  
sudo mount /dev/hdb5
would normally do it.

You say you just tried to format it? That'll erase it!

---

### Post by thespeth on 2007-02-24
Yeah, I saw that it was ntfs and I didn't think I could play with it in linux.

I already copied the files to another partition from hdb to hda, so everything's backed up.

Do you reccomend formatting to something more useful like fat 32 or keep it how it is?

---

### Post by thespeth on 2007-02-24
Hmmm...

> sudo mount /dev/hdb5
Password:
mount: /dev/disk/by-uuid/C8A8510FA850FCFE already mounted or /media/hdb5 busy
mount: according to mtab, /dev/hdb5 is already mounted on /media/hdb5

So did my computer automatically mount these partitions?  This is the first mount command I did, and now that I've looked into the media folder, I have other partitions already mounted, as well.

---

### Post by logos34 on 2007-02-24
Yep, it's already mounted (the fstab entry tells it to automount at startup).   Click on it--does it open?


> **thespeth said:**
> Yeah, I saw that it was ntfs and I didn't think I could play with it in linux.

I already copied the files to another partition from hdb to hda, so everything's backed up.

Do you reccomend formatting to something more useful like fat 32 or keep it how it is?

You can change it to fat32--that's probably the most popular option because then you can read and write to it from either OS.  Alternatively you can do what I and a growing number of people do--use NTFS-3G driver which allows you to write to NTFS.

edit: fs-driver (r+w to ext3) is something you might want to have for windows in case you want to access your linux root partition.

---

### Post by thespeth on 2007-02-24
I'm a photographer, and I'd like to start using uuntu full time with gimp.

But I'll keep your suggestions in mind for filesystems before I decie whether or not to get rid of xp.

Thanks for your help!

---

