---
title: "Mounting Extra Storage"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Usbman on 2007-07-01
I want to mount my spare internal HD onto my pc. I had disconnected it when I installed Ubuntu on 1st drive so keep things simple initially.

[IMG]http://img231.imageshack.us/img231/9308/asdzh0.gif[/IMG]

the diagram above is from gparted (of spare HD.. it's serial ata..)  and you can see there is a bit of the HD unallocated. The other drives are ntfs. fdisk -l shows

dev/sdb1   f       w95 Ext 1d(LBA)
"" ""/sdb5  7       NTFS
""
""
""

How do I mount it? Should I format the unallocated bit to ext3 or just point to sdb1 which is part of extended hard drive..?

---

### Post by annda on 2007-07-01
if you want to access the data on this drive (i suppose you do, otherwise you would format it), you need to mount each partition separately, which means 4 new entries in fstab. if you need any more info, just post here.

---

### Post by Usbman on 2007-07-01
thanks for that. I shall do that..

Yes I want access to the data on the drives.

---

### Post by Usbman on 2007-07-01
I added the line

/dev/sdb5 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=1002 0 1 

in fstab and rebooted. nothing.

---

### Post by logos34 on 2007-07-01
Read the bottom of [this page]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by Usbman on 2007-07-01
I changed the line removing "3g" and leaving the rest as the others and I've got access to sdb5 within the windows folder within media. 

If I do same for others, will it lump all files in those partitions there under 1 windows folder.. or will it organise them as sd8 etc.. otherwise i might as well unmount them and give them their own directory.

---

### Post by logos34 on 2007-07-01
so you don't want write access (ntfs-3g)?

I would put each partition on its own mount point, and maybe tack on a number to differentiate them, like:

/dev/sdb5 /media/window5 ...
/dev/sdb6 /media/windows6 ...

and so on

---

### Post by RTrev on 2007-07-01
> **Usbman said:**
> I changed the line removing "3g" and leaving the rest as the others and I've got access to sdb5 within the windows folder within media. 

If I do same for others, will it lump all files in those partitions there under 1 windows folder.. or will it organise them as sd8 etc.. otherwise i might as well unmount them and give them their own directory.

I think you can control all that by specifying the mount points in fstab.  Just create folders somewhere, I normally use my home directory, and give them a name, and use fstab to point each partition to each of the distinct mount points.

---

### Post by Usbman on 2007-07-01
Ok I created directories and pointed to them in fstab and mounted the drives. But they're only read-only, read somewhere ntfs is only read-only in ubuntu.. I cannot write to those drives or save files yet. 

That's the next task.

---

### Post by Usbman on 2007-07-01
Can one backup files on the ntfs drive to dvd-r and then format them into ext3/fat32 so they can be used in ubuntu?

---

