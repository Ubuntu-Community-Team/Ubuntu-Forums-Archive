---
title: "Can you access the hard drive from a live cd?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by ducamie on 2007-02-12
Can I access my hard drive from the ubuntu edgy live cd?

Ive just upgraded my motherboard and i cant get to my hard drive to rescue a few files i need before i reinstall ubuntu.

---

### Post by mitanc on 2007-02-12
Sure can.  If it is not already detected, you should be able to easily mount the partition and do what you need to do.  I recently had a problem with my laptop and a huge magnet that got stuck to the  portion directly above my hard drive.  The drive's data was mostly intact, but Windows on that machine would not boot.  I was able to use the live cd to get in and copy my important data to a portable harddrive.  Ubuntu to the rescue!

Good luck.

---

### Post by ducamie on 2007-02-12
thanks for the reply!

where will i find the drive if it has been mounted automatically?

what sudo command do i use to mount it if its not? its an ide drive.

---

### Post by ducamie on 2007-02-12
anyone?? this is really important.

---

### Post by Archmage on 2007-02-12
Please enter "mount" in the command line. There you should see what partition is mounted and what mount point it has.

---

### Post by ducamie on 2007-02-12
hey

it isnt automatically mounted

what do i need to type to mount it?

---

### Post by meborc on 2007-02-12
try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

EDIT: the link is for ntfs filesystem, but you will get the point so you can modify the commands to fit your filesystem

---

