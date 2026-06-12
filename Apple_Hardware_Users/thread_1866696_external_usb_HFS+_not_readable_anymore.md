---
title: "external usb HFS+ not readable anymore"
date: 2011-10-21
forum: Apple Hardware Users
---

### Post by macdalor on 2011-10-21
Hello!

I'm having a problem with an external WD 3TB Ext USB HD which I use as a back up to a Lacie 5Big which is currently gone to repair (apparently trouble never comes alone!) so I am extremely keen on retrieving the data the WD holds as this is my back up...:(

The WD drive was working fine for about 2 month (since I bought it) until yesterday morning when my MBP started giving me a message saying that this drive wasn't readable and asking me to initialize, ignore or eject, the typical msg given with a non-formated drive.

No ticking or other noises...

After trying what I could from OSX (mainly OSX  Disk Utility, Techtool and disk warrior) I've decided to check it out in ubuntu and ran the following:

> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x12abbdd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       45600  2930233340   ee  GPT
Partition 1 does not start on physical sector boundary.
> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" 
/dev/sda2: UUID="05286d32-220c-3a79-8d99-e3749dd2b269" LABEL="Traktor" TYPE="hfsplus" 
/dev/sda3: UUID="67aa9d18-6783-3b2a-bbdd-0d2467b16d36" LABEL="General" TYPE="hfsplus" 
/dev/sda4: UUID="76580f53-a162-3b20-8fdf-50e3da540b8c" LABEL="Logic" TYPE="hfsplus" 
/dev/sda5: UUID="db43304c-b14e-3f6d-ae5b-57a500f6ffcf" LABEL="Data" TYPE="hfsplus" 
and tried to mount the drive as followed:

> 
ubuntu@ubuntu:~$ ls /media 
cdrom  Data  sdb1
> ubuntu@ubuntu:~$ sudo mount -t squashfs /dev/sdb1 /media/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


And have ran:

> 
ubuntu@ubuntu:~$ sudo fsck.hfsplus /dev/sdb1
** /dev/sdb1
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
   Invalid node structure
(4, 1079)
** Volume check failed.


Any idea on 1) what is this "invalid node structure"? 2) how to fix the FS on that drive if ever possible? 3) Any other ideas?

Just thought I'd update as I am still trying to sort this out and ran this command from my OSX terminal:
> $ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Traktor                 30.0 GB    disk0s2
   3:                  Apple_HFS General                 30.0 GB    disk0s3
   4:                  Apple_HFS Logic                   250.0 GB   disk0s4
   5:                  Apple_HFS Data                    189.4 GB   disk0s5
/dev/disk3
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *3.0 TB     disk3
   1:       Microsoft Basic Data                         3.0 TB     disk3s1


Microsoft Basic Data?!?! isn't that strange!?? I've tried finding out how to switch back to HFS+ but no luck...

> 
sudo gpt show -l /dev/disk3
      start       size  index  contents
          0          1         PMBR
          1          1         Pri GPT header
          2          4         Pri GPT table
          6        250         
        256  732557824      1  GPT part - "Drive"
  732558080        251         
  732558331          4         Sec GPT table
  732558335          1         Sec GPT header


Anyone please?

---

