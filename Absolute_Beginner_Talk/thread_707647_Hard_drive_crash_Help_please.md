---
title: "Hard drive crash? Help please"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Amstell on 2008-02-25
So i woke up this morning and my computer was frozen.  Restart and it got to a black screen that said no boot option available.  Press F1 to restart and F2 for BIOS options.  

So i checked my bios and everything looked good.  No problems with the order or anything

Tried to run SuperGrub to restore my MBR or lilo but that didn't work. 

So I inserted my 7.10 live cd.  Everything loaded up just fine but my partitions are gone.  So I loaded up the partition manager and all it was is 233gb unallocated data.  No mention of my /home or / ext3 or my swap partition.  

The computer is only about a year old and is a dell E521.  Never had any problems with it.

Did my HD just crap out on me and is there anyway to recover the data, there is a lot on there.

Thanks for the reply's hopefully this is just a small glitch but somehow I don't think it is.

Cheers

---

### Post by Amstell on 2008-02-25
if I run gparted and do refresh devices it crashes....sounds like my hard drive is done

---

### Post by herbster on 2008-02-25
Try this in live cd and paste output:

```
sudo fdisk -l
```

Can you open up your box and check the physical connections (assuming you know how to do this, otherwise don't even think about it)? If it's really dead there's not much to do AFAIK. I hope you don't lose all your stuff as I did with my drive that crapped out on me a few weeks back :)

---

### Post by Amstell on 2008-02-25
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3da7f964

Disk /dev/sda doesn't contain a valid partition table

---

### Post by herbster on 2008-02-25
Are you capable of removing the drive from your computer? If this would void any warranty or anything (I don't know Dell's policies) please do not even think about it, but if you're 100% sure it is within the warranty you have, then take it out and try to put it in another computer with Windows. What I do is install the FS driver (here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)) on the Windows box, reboot that, then you can go into Control Panel > IFS Drives and see any linux partitions and mount them. That would at least tell you that it works.

Of course I'm assuming you don't have another linux box to do this with, if you do by all means try it with that as well. Someone may have a better idea but I'm trying to suggest something that wouldn't affect any data on the drive at all.

---

### Post by ByteJuggler on 2008-02-25
It might be possible to recover (some of) your data, but some important advice:  Do **_*not*_** try to fix/recover any data *on* the broken disk, do nothing that writes to the disk!

The best approach is to acquire another hard disk of greater size than the dying disk, then to image the dying disk onto the healthy disk, and only *then* do you attempt recovery of files or the filesystem onto another/third disk (or another partition on the new disk.) 

To image your dying disk, there's a program called "ddrescue" that will copy everything it can easily read quickly, and will then try as hard as it can to read the bad parts of the disk, in a non-linear fashion, to maximise recovery chances.

There are Linux distributions dedicated to recovery situations, such as the[ Trinity Resuce Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"), which is one I particularly like, but that said, you can do many things even with just the Ubuntu LiveCD and an internet connection (to install packages from.)   In any case, the Trinity rescue website documents many of these procedures in more detail, see for example [here]("http://trinityhome.org/Home/index.php?wpid=59&front_id=12").  (Obviously the comments about temperature is probably not that relevant in your case.)

Once the disk has been cloned, you should try normal filesystem recovery utilities, such as fsck, preceded by  [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") first if your partition table is missing (as seems to be the case in your case), and possibly as a last resort [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (which does not depend on the filesystem to recover files), to recover your files if the filesystem is not repairable by fsck.  I/we can advise further in this regard depending on what you decide to do.

---

### Post by Amstell on 2008-02-25
whenever i run

sudo fsk /dev/sda i get

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by Amstell on 2008-02-25
> **ByteJuggler said:**
> It might be possible to recover (some of) your data, but some important advice:  Do **_*not*_** try to fix/recover any data *on* the broken disk, do nothing that writes to the disk!

The best approach is to acquire another hard disk of greater size than the dying disk, then to image the dying disk onto the healthy disk, and only *then* do you attempt recovery of files or the filesystem onto another/third disk (or another partition on the new disk.) 

To image your dying disk, there's a program called "ddrescue" that will copy everything it can easily read quickly, and will then try as hard as it can to read the bad parts of the disk, in a non-linear fashion, to maximise recovery chances.

There are Linux distributions dedicated to recovery situations, such as the[ Trinity Resuce Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"), which is one I particularly like, but that said, you can do many things even with just the Ubuntu LiveCD and an internet connection (to install packages from.)   In any case, the Trinity rescue website documents many of these procedures in more detail, see for example [here]("http://trinityhome.org/Home/index.php?wpid=59&front_id=12").  (Obviously the comments about temperature is probably not that relevant in your case.)

Once the disk has been cloned, you should try normal filesystem recovery utilities, such as fsck, preceded by  [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") first if your partition table is missing (as seems to be the case in your case), and possibly as a last resort [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (which does not depend on the filesystem to recover files), to recover your files if the filesystem is not repairable by fsck.  I/we can advise further in this regard depending on what you decide to do.



Thanks for your advice that was exactly what i needed to do.  I ran testdisk and my partition files got all screwed up so I rewrote those and super grubbed my mbr back to normal.  Now I would like to run some tests to make sure everything is fine.

What is the best way to do that?

---

### Post by ByteJuggler on 2008-02-25
> **Amstell said:**
> Thanks for your advice that was exactly what i needed to do.  I ran testdisk and my partition files got all screwed up so I rewrote those and super grubbed my mbr back to normal.  Now I would like to run some tests to make sure everything is fine.

What is the best way to do that?

Ok... so you have your partition table back?  I'm still a bit worried that you have actual physical hard disk problems, in which case running fsck etc might make things worse... fortunately testdisk only rewrites the partition table and Super Grub the MBR, so it doesn't touch much of the disk... it also likewise doesn't really give you an indications of wether you have disk problems elsewhere on the disk... anyway, my suggestions:

1.) Backup any data that isn't backed up that you cannot afford to lose *now*.  No if's, no but's. 
2.) Then, once you've done that, boot from your LiveCD, then issue the following command at a prompt:

```
sudo fsck -fr /dev/sda1
```

Where you must replace "/dev/sda1" with your Linux partition location.  ("-f" means "force", e.g. "check filesystem even if marked clean" and "-r" means "recover" e.g. "interactively fix errors.")

Next do:

```
sudo badblocks -f /dev/sda1
```

Again replace /dev/sda1 with your partition.  This will scan for bad blocks on the disk.  I would stop/bail on the first sign of any trouble and get myself a new disk pronto if any bad blocks are found, and then image your existing installation over to the new disk, after which you can swap drives and boot from the new disk.  (I'll explain how to image over if you want, if you decide to follow that route. )

---

### Post by Amstell on 2008-02-25
> **ByteJuggler said:**
> Ok... so you have your partition table back?  I'm still a bit worried that you have actual physical hard disk problems, in which case running fsck etc might make things worse... fortunately testdisk only rewrites the partition table and Super Grub the MBR, so it doesn't touch much of the disk... it also likewise doesn't really give you an indications of wether you have disk problems elsewhere on the disk... anyway, my suggestions:

1.) Backup any data that isn't backed up that you cannot afford to lose *now*.  No if's, no but's. 
2.) Then, once you've done that, boot from your LiveCD, then issue the following command at a prompt:

```
sudo fsck -fr /dev/sda1
```

Where you must replace "/dev/sda1" with your Linux partition location.  ("-f" means "force", e.g. "check filesystem even if marked clean" and "-r" means "recover" e.g. "interactively fix errors.")

Next do:

```
sudo badblocks -f /dev/sda1
```

Again replace /dev/sda1 with your partition.  This will scan for bad blocks on the disk.  I would stop/bail on the first sign of any trouble and get myself a new disk pronto if any bad blocks are found, and then image your existing installation over to the new disk, after which you can swap drives and boot from the new disk.  (I'll explain how to image over if you want, if you decide to follow that route. )

Thanks for your help.  I'm back up now and will probably work on this tonight.

---

