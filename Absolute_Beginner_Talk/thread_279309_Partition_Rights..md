---
title: "Partition Rights."
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by james.gornall on 2006-10-17
Hi again, once more I'm having problems with my newly created partition.

Now I can see it I am unable to put files in or create folders cause I don't have the rights to.

How can I change this please?

---

### Post by taurus on 2006-10-17
You don't want to change permissions to your /!  Not a good idea.  Instead, you use the "sudo" with the command.  For instance, if you want to rename "test" in /etc, then you can do it from a terminal, Applications -> Accessories -> Termina,

```
sudo mv /etc/test /etc/TEST
(and use the same password that you log in with...)
```

---

### Post by james.gornall on 2006-10-17
so everytime I wanna put music on the drive Ill need to use that?  or is it only when creating folders?

---

### Post by taurus on 2006-10-17
It depends on where you want to store your music!  Can you tell me where you plan to store your music on your Ubuntu.  Maybe changing permission is the best solution but before I show you how to do that, I need to know where to make sure you don't change any permission to your system files.

---

### Post by james.gornall on 2006-10-17
kk so I mnted my new partition to 

/mnt/folder

then music is in /mnt/folder/music

Is that what you meant?

---

### Post by james.gornall on 2006-10-17
hate to bump, just seems to be flying down the page.

Sorry :confused:

---

### Post by starsky on 2006-10-17
> **james.gornall said:**
> kk so I mnted my new partition to 

/mnt/folder

then music is in /mnt/folder/music

Is that what you meant?

press ALT+F2 then type xterm or you can use konsole or gnome-terminal, whichever you want. Use one. :)

now, type these commands (don't worry it's only 1 time process):
1. cd /media 

2a. sudo mkdir cdrom
2b. sudo mkdir windows
2c. sudo mkdir usb
2d. sudo mkdir windows-share

3a. sudo mount -t iso9660 /dev/cdrom /media/cdrom (for copying from cdrom)
3b. sudo mount -ro -t ntfs /dev/<your_windows_partition**> /media/windows (for copying from windows partition, see note below)
3c. sudo mount -t vfat /dev/<your_usb_device> /media/usb (this mount command assumes you are using usb pen drive which are mostly found to be formatted as fat (file allocation table file system. including **ipod**. <winks>)
3d. mount -t smbfs //<your_windows_share_ip_address_or_alias>/<share_name> /media/windows-share/ (for files in your windows share)

4. and now, copy, delete (I do not know the state-of-affairs of writing to ntfs i.e., whether ntfs write is safe/not ), play, do whatever you desire.

*******
NOTE

 - to know windows partition, do this in the xterm -
    "sudo parted /dev/[s-h]da print". s or h depending on whether your disk drive is SCSI or standard IDE. Now it'll print the partitions on your hard drive. It'll print out something like -

$ sudo parted /dev/sda print
Disk geometry for /dev/sda: 0kB - 60GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    7GB     7GB      primary   ntfs         boot
2       47GB    57GB   57GB    primary   ext3
3       59GB    65GB    526MB   primary   linux-swap
Information: Don't forget to update /etc/fstab, if necessary.

so you can see that my windows partition is /dev/sda1. ext3 is /dev/sda2 and /dev/sda3 is swap.


    - Also, anything mounted under /media is automagically displayed on your desktop in breezy and dapper.

*******


hope this helps.

---

### Post by james.gornall on 2006-10-17
Ok, I just noticed I was trying to use the NTFS drive.

I've created my new linux partition in its place.

I've mounted it in same place only under hdb4

result of fdisk -l

```
gornall@gornall-desktop:/mnt$ sudo fdisk -l
Password:

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1530    12289693+  83  Linux
/dev/hdb2            1531        1606      610470   82  Linux swap / Solaris
/dev/hdb3            1607       11167    76798732+   7  HPFS/NTFS
/dev/hdb4           11168       14593    27519345   83  Linux



```

so I have 

```
sudo mount /dev/hdb4 /mnt/folder

```

Now I just want rights to that part of the drive.

---

### Post by starsky on 2006-10-17
Replace 
```

sudo mount /dev/hdb4 /mnt/folder

```

with

```

sudo mount -ro -t ntfs /dev/hdb3 /mnt/folder

```

hope it helps.

---

