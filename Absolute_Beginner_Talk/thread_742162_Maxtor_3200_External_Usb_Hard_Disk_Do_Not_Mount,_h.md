---
title: "Maxtor 3200 External Usb Hard Disk Do Not Mount, how do i know if it's broken?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Netrunner on 2008-04-01
as in the title i got this 3200 maxtor from a friend.
it's 500 gb in size.
ntfs partitioned.

when i plug it in windows it makes sound but i can't see anything...
when i plug it in linux i know only that:
lsusb:
Bus 004 Device 007: ID 0d49:3200 Maxtor

fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes 
etcetcetc
Partition table entries are not in disk order
and this is for my linux partitions...

but i do not have any /dev/sdb* entry for the external ntfs...

should i presume that all the data inside is lost?
can someone address me to a solution?
Because the warranty expired i also tryed to plug it into a case...
With no results...
 lspci: 
not found any 3200 maxtor sign of life 
fdisk -l 
nothing

Thanks in advice.

---

### Post by ghost_ryder35 on 2008-04-01
do you have "ntfs-3g"?

---

### Post by Netrunner on 2008-04-02
> **ghost_ryder35 said:**
> do you have "ntfs-3g"?

sorry i didn't mentioned.
i have it and i tryed to mount the disk with it guessing the device but i had no luck.
perhaps there is a way to recreate the table partition and keep the data?
or perhaps it's just broken irreversibly.
Should i hear a strange sound from the disk?

---

### Post by superprash2003 on 2008-04-02
create a folder say /home/[user]/usbhdd .. then type sudo mount /dev/sda /home/[user]/usbhdd .. what happens?

---

### Post by Netrunner on 2008-04-08
> **superprash2003 said:**
> create a folder say /home/[user]/usbhdd .. then type sudo mount /dev/sda /home/[user]/usbhdd .. what happens?

well /dev/sda is where i have root partition, and is the internal hd...
it happens exacty that it is already mounted =)
/dev/sda already mounted or /home/[user]/usbhdd busy


but if i type:
sudo mount /dev/sdb /home/[user]/usbhdd
special device /dev/sdb does not exist

so i guess it's broken...

thank you for the answers

---

