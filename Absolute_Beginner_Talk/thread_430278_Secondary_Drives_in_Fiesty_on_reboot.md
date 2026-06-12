---
title: "Secondary Drives in Fiesty on reboot"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by DennShin on 2007-05-02
Hi guys, 
     I have two seperate drives from the main ubuntu drive.  One is fat32 the other is ntfs.  Now I know how to mount them and use them but after installing Fiesty they change after every reboot. hdb1 and sdb1 change to sdc1 and sda1.  Any idea why?  I am at work atm so I cannot post an fstab or fdisk until I get home.

---

### Post by gerscht on 2007-05-02
As far as I can remember is feisty using the scsi subsystem all the way through, so all drives will start with *s*.
To be on the save side, use the UUIDs of your drives, this will also make sure that an external hard disk is always mounted in the same place.

Gerscht

---

