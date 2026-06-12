---
title: "is this ok for a daul boot?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2007-03-30
hi

i am doing a dual boot between windows and ubuntu. does this setup look ok, and will i lose any data?


Language: English
 Keyboard layout: United Kingdom
 Name: brady
 Login name: adminaccount
 Location: Europe/London
 Migration Assistant:
 Microsoft Windows XP Professional (/dev/sda1):
None




If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #3 of SCSI1 (0,0,0) (sda) as swap
 partition #4 of SCSI1 (0,0,0) (sda) as ext2

many, thanks.

---

### Post by richbarna on 2007-03-30
> **smile-its-smiley said:**
> hi

i am doing a dual boot between windows and ubuntu. does this setup look ok, and will i lose any data?


Language: English
 Keyboard layout: United Kingdom
 Name: brady
 Login name: adminaccount
 Location: Europe/London
 Migration Assistant:
 Microsoft Windows XP Professional (/dev/sda1):
None




If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #3 of SCSI1 (0,0,0) (sda) as swap
 partition #4 of SCSI1 (0,0,0) (sda) as ext2

many, thanks.

Yep! Looks fine, apart from the Ext 2 choice, should be Ext3. The most important part is when it says which partitions will be formatted, you only have the root and the swap, so no problem. (strange how you have swap before the root, but not important) ;)

---

