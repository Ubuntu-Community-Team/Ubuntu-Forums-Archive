---
title: "NTFS partition and Ubuntu"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-06-12
Hello,

I blasted Windows XP about 2 months ago. I had set up 2 partitions, one for windows and another for storing important files and such. Well I got sick of windows and installed Ubuntu over the windows partition. I still have that other partition of important files but it is in NTFS format. 

Is there anyway to access those files from Ubuntu? I'm thinking not...I guess that was a pretty stupid move. But still, even if I lost it all, it was worth finally giving up Windows.

Thanks,

Maria

---

### Post by aysiu on 2006-06-12
Sure, you can access it.

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

### Post by glotz on 2006-06-12
Also, I think you can now convert the disk to a better native filesystem, system > admin > gnome partition editor. Probably faster access, writing capability, journaling to reduce errors, reduced fragmentation, etc. I wonder how long would this process take? Probably depends on the size of the disk. (I myself have and older computer and 2 40gig disks but no windows and I'd like to convert them myself.) (Be advised though, partitioning is a potentially hazardous undertaking and your own mistake or a power failure, etc might result lose you your data. The tools itself work pretty well and have been around for some time.)

---

### Post by aysiu on 2006-06-12
You'd want to back up your files from the NTFS drive first before changing it to Ext3.

---

### Post by Maria_Firewire on 2006-06-12
Thanks! Ubuntu (and the Ubuntu community) ROCKS!

Maria  :D

---

