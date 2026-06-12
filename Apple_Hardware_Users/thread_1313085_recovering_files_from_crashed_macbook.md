---
title: "recovering files from crashed macbook"
date: 2009-11-03
forum: Apple Hardware Users
---

### Post by cathor on 2009-11-03
Hi!

I am trying to mount an internal drive (HFS +?) using a ubuntu live cd but cant get it to work. The disk is 120 gb. Since i cant copy/paste the reports i will try to write them out as accurately as possible. 

sudo mount -t hfsplus /dev/sda /mnt/macosx
> 

mount: wrong fs type, bad option, bad superblock on dev/sda/
missing codepage or other error
In some cases useful info is sound in syslog - try
dmesg tail or so.

sudo fdisk -l gives
> 

Disk /dev/sda: 120.0 GB. xxxxxxxxxxxbytes

     Device Boot       Start               End            Blocks              Id     System
    /dev/sda1                1           14594        xxxxxxxx              ee    EFI GPT

dmesg tail gives:
> 

sda :mode sense 00 3a 00 00
SCSI device sda: write cache: enabled, read cache: enabled doesnt support DPO or FUA
hfs: unable to find HFS+ superblock
hfs: unable to find HFS+ superblock
hfs: unable to find HFS+ superblock
hfs: unable to find HFS+ superblock
hfs: cant find a HFS filesystem on dev sda
hfs: cant find a HFS filesystem on dev sda1
hfs: cant find a HFS filesystem on dev sda2
applesmc: wait statusfailed c != 8

sudo ls alh /dev gives:
> 

...
brw-rw----       1        root       disk        8.         0         sda
brw-rw----       1        root       disk        8.         1         sda1
brw-rw----       1        root       disk        8.         2         sda2
...

sudo /sbin/parted (print) gives:
> 

...
Using /dev/sda
...
Disk /dev/sda: 120 GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

1     20,5kb    210mb    fat32       EFI system partition       boot
2     210mb    120GB    hfs+        Customer

Would really appreciate some guidance here...

Thanks in advance

---

### Post by aysiu on 2009-11-03
Ubuntu should be able to mount HFS+ as read-only.

Perhaps the drive is corrupted. In that case, I would install the *testdisk* package and use ```
sudo photorec
``` to recover the files.

More details here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

