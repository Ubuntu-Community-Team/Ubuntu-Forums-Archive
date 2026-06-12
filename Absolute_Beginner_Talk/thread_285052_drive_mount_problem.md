---
title: "drive mount problem"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-26
I have kubuntu 6.06
On my hard disk I created a fat32 drive from windows after kubuntu was installed.

I cannot open that drive(see the image attachment)

I can access my other ntfs drives which were there before
I installed Kubuntu.

please help

---

### Post by John.Michael.Kane on 2006-10-26
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Ecthelion on 2006-10-26
You should add a line in your fstab

```
sudo gedit /etc/fstab
```

> /dev/<disknumber>       /media/<mountpointname>   vfat    defaults        0       2

replacing disknumber by hdb? or sda? (? is the number)
and <mountpointname> by the name of the dir you want it to be mounted
if that dir isn't there yet use
```
sudo mkdir /media/<mountpointname>
```

this should give you read-acces to the disk.
You can also write to it as root

There's a way to read/write as normal user, but I don't have it right here

---

### Post by Ecthelion on 2006-10-26
hmmm

>  	[http://ubuntuguide.org/wiki/Dapper#H...read.2](http://ubuntuguide.org/wiki/Dapper#H...read.2) Fwrite
[http://ubuntuguide.org/wiki/Dapper#H...o_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#H...o_read.2Fwrite)

these are great links...
Usefull for me too!
tx

---

