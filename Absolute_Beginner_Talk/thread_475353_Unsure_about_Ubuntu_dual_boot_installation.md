---
title: "Unsure about Ubuntu dual boot installation"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Minstrover on 2007-06-16
Language: English
Keyboard layout: U.S. English
Name:
Login name:
Location:
Migration Assistant:
Microsoft Windows XP Professional (/dev/sda1):


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
partition #3 of SCSI1 (0,0,0) (sda) as ext3
partition #5 of SCSI1 (0,0,0) (sda) as swap

What does it mean by 'The following partitions are going to be formatted:'
I don't want to lose any data will this affect my files i use on XP?

Thanks

---

### Post by dbbolton on 2007-06-16
> **Minstrover said:**
> Language: English
Keyboard layout: U.S. English
Name:
Login name:
Location:
Migration Assistant:
Microsoft Windows XP Professional (/dev/sda1):


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
partition #3 of SCSI1 (0,0,0) (sda) as ext3
partition #5 of SCSI1 (0,0,0) (sda) as swap

What does it mean by 'The following partitions are going to be formatted:'
I don't want to lose any data will this affect my files i use on XP?

Thanks
well, as long as you don't have any data on partitions 3 and 5, it won't erase any of your data from XP. when the partitioner creates new partitions, they must be formatted before they can be used.

if you want to be extra safe, back up all your important data before installing ubuntu. if you want to be totally safe, don't install it at all.

---

