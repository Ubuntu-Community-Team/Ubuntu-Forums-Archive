---
title: "Added mounted partition to desktop and nautilus"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by rickmans on 2006-11-12
I mounted one of my partitions (sda3) after the installation of Edgy, however it does not show up on my desktop and in nautilus. So I would like to see the hd pop up here:

[img]http://images.fok.nl/upload/061112_15029_desktop.jpg[/img]

and here:

[img]http://images.fok.nl/upload/061112_15029_nautilus.jpg[/img]

any ideas?

---

### Post by dbott67 on 2006-11-12
Apparently, the trick is to create the mount point in /media if you want it to show up on the Destkop.

-Dave

---

### Post by dbott67 on 2006-11-12
There's also a setting in gconf-editor that shows volumes on the Desktop.

---

### Post by Ksmith3637 on 2006-11-12
ok so where do you find this.. says it is installed in add/remove..??
thanks..

my other 4 drives are not shown anywhere but are in the /dev section how do i get them to show.. 2 sata  2 ide  all NTFS..

thanks

---

### Post by kewldude606 on 2006-11-12
> **Ksmith3637 said:**
> ok so where do you find this.. says it is installed in add/remove..??
thanks..

my other 4 drives are not shown anywhere but are in the /dev section how do i get them to show.. 2 sata  2 ide  all NTFS..

thanks

To use the gconf-editor, press Alt-F2 and type in gconf-editor and press enter.

For the NTFS drives, you will have to install the NTFS driver.  This driver is not 100% stable!  You risk loosing data.  If you can, convert the drives/partitions to FAT32, which is readable by Windows and Linux.  Check out this wiki page: [https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

### Post by dbott67 on 2006-11-12
You can also right-click the 'Applications' menu & select 'Edit Menus', then browse to APPLICATIONS > SYSTEM TOOLS.  Place a check mark in the 'Configuration Editor'.

-Dave

---

### Post by rickmans on 2006-11-13
The mount point was in /media, I tried a killall nautilus to force a reload, however nothing happened. After a reboot the mounted disks did appear again on the desktop and in nautilus.

---

