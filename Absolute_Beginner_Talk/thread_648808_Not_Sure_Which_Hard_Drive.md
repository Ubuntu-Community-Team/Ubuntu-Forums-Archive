---
title: "Not Sure Which Hard Drive"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Lanc1988 on 2007-12-24
I am installing ubuntu 7.10 on my desktop computer which has two hard drives that are exactly the same. On one hard drive I have vista and the other one has nothing on it right now so I want to install ubuntu on that one.

The problem is that when I double click install and get to the prepare disk space step and choose the 'use entire disk' option, both hard drives listed are exactly the same, they both say:

SCSI3 (0,0,0) (sda) - 250.1 GB ATA HDS722525VLSA80
SCSI4 (0,0,0) (sdb) - 250.1 GB ATA HDS722525VLSA80

I kind of assume that it would be the 2nd one, the sdb because when i select it and click 'Forward' it says 'there were no users or operating systems suitable for importing from' and when i select the sda it goes immediately to the 'Who are you' screen, but I want to make sure that I dont overwrite the vista hard drive and lose everything.. is there some way to tell which is which?

---

### Post by autocrosser on 2007-12-24
The system will normally go by the bios settings--so your boot disk would be sda (master) & sdb (slave or 2nd disk). 

In the liveCD you will find a app called "Partition Editor or Gparted"--open the app up & look at both disks--one will show a percentage full & the other one won't--they will also be listed by the sda/sdb naming. 

Don't partition with the app unless you know what you are doing--just use it to look--

---

### Post by forestpixie on 2007-12-24
open aterminal - in apps>accessories 

and do
```
sudo fdisk -l
```

---

### Post by hyper_ch on 2007-12-24
I'd go with gparted... once you find the partition where there is no data on it, you can either manually set the desired partitions or delete any partitions and leave the drive unpartitioned. For the latter you can then select "use largest continouuse free space" or something like that... for the first one you'd then do a manual partitioning.

---

