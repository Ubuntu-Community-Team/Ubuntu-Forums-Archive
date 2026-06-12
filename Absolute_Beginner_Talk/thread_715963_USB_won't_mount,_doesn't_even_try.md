---
title: "USB won't mount, doesn't even try"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by balornt on 2008-03-05
I am a newb at linux. I plugged in my usb drive today and nothing happened. It doesn't try to mount, much less fails to mount. I have four different usb ports and three of them used to work fine. Then I downloaded an update and now it doesn't mount automatically. Someone tell me how to mount it manually. I looked at other posts/forums and got nowhere. Here are the results from lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by taurus on 2008-03-05
Can you at least mount it by hand from a terminal?  What filesystem is your USB drive?

```
sudo fdisk -l
```

---

### Post by jhawl on 2008-03-05
this may be a major newb post but i just had that problem with my external usb dvd burner, and rebooting my computer seemed to do the trick

---

### Post by nmartine on 2008-03-05
Try plugging it into a windows machine and safeley remove it.  Then it should be mountable.

---

### Post by balornt on 2008-03-05
My usb drive is FAT

Here is fdisk results:

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6817    54757521   83  Linux
/dev/sda2            6818        7113     2377620    5  Extended
/dev/sda5            6818        7113     2377588+  82  Linux swap / Solaris

---

### Post by balornt on 2008-03-05
i have safely removed and restarting didn't do anything

---

