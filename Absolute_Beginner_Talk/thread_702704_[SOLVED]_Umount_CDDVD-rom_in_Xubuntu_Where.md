---
title: "[SOLVED] Umount CD/DVD-rom in Xubuntu? Where?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-20
Hi, I have some problem with my CD/DVD-rom.

Since my laptop doesn't have a CD/DVD-rom with it, I have to use a USB-plugin one. However, I put a CD in (well, a Xubuntu one) and then the CD shows on my Desktop. However, after I eject the CD and that figure just disappears. But then, where can I find the CD/DVD-rom figure and efect the ROM itself? I go to /media folder and there are two cdrom. One is cdrom and the other is cdrom0. Both of them are empty. Now, I'm just trying again with Xubuntu installation CD in. Then, both cdrom and cdrom0 get the CD content!!! So when I eject this CD-ROM, which one should I umont with? And why are there two? What's the difference?
Thanks in advance!

---

### Post by incen on 2008-02-20
Well... I think I got some trouble. I umount the cdrom with the command what my advisor told me to do with memory stick. I do this:
sudo umonut -t vfat /media/sda1 /media/chrom

And then, I accidently umount sda1.... :(
I tried to mount it back with
sudo monut -t vfat /media/sda1
but it just didn't work.

Did I do something harmful to my system? Can this problem be fixed by just reboot?

---

### Post by jan quark on 2008-02-20
first

it is normal that the cd icon disappears after the cd is ejected, and appears when you insert the cd
don't worry

second

the folder with the arrow is only a link to the folder
the folder without the arrow is the actual mounting point of the cd

---

### Post by jan quark on 2008-02-20
please do not shut down

post the output of 

```
cat /etc/fstab
```

```
sudo fdisk -l
```

---

### Post by incen on 2008-02-20
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a6a57e49-362e-4b9e-8bc3-8ef701ed76b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=36A0FDF9A0FDC003 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=1B33-0A00  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=D156-6BD8  /winlin         vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=21d3c4b5-5151-4f12-861d-33af6df340d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

sudo fdisk -l
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2551    20487568+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4244        4864     4982040   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            2552        3158     4875727+   b  W95 FAT32
/dev/sda4            3159        4243     8715262+   5  Extended
/dev/sda5            3159        3267      875511   82  Linux swap / Solaris
/dev/sda6            3268        4243     7839688+  83  Linux

Partition table entries are not in disk order
```

Thanks!

---

### Post by incen on 2008-02-20
Does it mean that my sda1 is still there? I don't know how to read fstab though. Probably this is a good chance to start.

So it seems /dev/sda1 is my Windows partition and it is mounted as /media/sda1, right?
Right now I'm clicking on it, it says, "Cannot mount volume"...... :(

---

### Post by jan quark on 2008-02-20
well if you typed really this

> sudo umonut -t vfat /media/sda1 /media/chrom

And then, I accidently umount sda1....
I tried to mount it back with
sudo monut -t vfat /media/sda1
but it just didn't work.

then nothing happened because the command was false

it is not umonut

but

umount

and not monut

but 

mount


be careful with these commands and always ask before operating with them

---

### Post by incen on 2008-02-20
Well... I think I was just so nervous while posting. Yes, I typed "umount" so now I lost my Windows drive that shows on my Desktop. It's there but I cannot open it. It just gives me, "Cannot mount volume" and "Unable to mound ...". So I think it's seriously not there. What should I do then?

I'm not sure if I can ask such dumb thing like this so I tried it by myself first. And then..... blabla....

---

### Post by jan quark on 2008-02-20
ok 

one step at a time

please post the result of this

```
ls /media
```

---

### Post by incen on 2008-02-20
Now, I list /media:
```
cdrom  cdrom0  floppy  floppy0  sda1  sda2
```

However, when I do cd /sda1:
it's empty.

---

### Post by jan quark on 2008-02-20
run this

```
sudo mount /dev/sda1 /media/sda1 -t ntfs -o nls=utf8,umask=000
```

---

