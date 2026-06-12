---
title: "How do I find device name for USB key"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by muguwmp67 on 2007-01-27
I'm trying to repartition and format my USB key through ubuntu, all of the commands I've seen refer to the key as /dev/sda1.  Since that name refers to one of my SATA hard drives, I know I'm going to need the /dev/xxxx for the USB key.

Ubuntu recognizes the key and I'm wondering if there is a straightforward way to identify the device name, without checking each /dev/sd* entry individually.

---

### Post by chalex on 2007-01-27
From the command line you can type "sudo fdisk -l" which will list all the partitions on all your disks.    Or you can type "tail /var/log/messages" after you connect the USB key.

I'm not really familiar with the GUI, but can't you just right-click->properties after you connect the USB flash drive?

Edit: also, System->Administration->Disks, but I'm on Dapper.

---

### Post by muguwmp67 on 2007-01-27
Nah, I tried right-clicking in nautilus.  Device name isn't listed in properties.

sudo fdsisk -l does the trick, and if I leave the sudo off, then it only lists the usb drive.

Perfect!

---

