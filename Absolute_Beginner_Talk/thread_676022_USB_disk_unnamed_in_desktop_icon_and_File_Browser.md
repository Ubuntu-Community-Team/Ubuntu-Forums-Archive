---
title: "USB disk unnamed in desktop icon and File Browser"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by LittleTyke on 2008-01-23
I've just installed 7.10. I have two USB sticks, a Verbatim Store'n'Go and a Buffalo. When  I insert the Verbatim the desktop icon says "STORE'N'GO" and File Browser, under Places, says the same. When I unmount the stick, the desktop icon disappears (as expected) and File Browser now says "Verbatim Store 'n' Go", also as expected, as the stick is still inserted.

Now when I insert the Buffalo stick instead, watching File Browser while I do so, File Browser *briefly* flashes up "BUFFALO USB Flash Disk" and then that changes almost immediately to just "disk". The desktop icon reads "disk". When I unmount the Buffalo stick, the desktop icon disappears and File Browser now says "BUFFALO USB Flash Disk" constantly.

1. Why is the behaviour different for each stick?

2. How can I get the Buffalo stick to behave like the Verbatim, i.e. the desktop icon and the File Browser entry reflect the stick's name, whether inserted and mounted or inserted and unmounted?

---

### Post by mridkash on 2008-01-23
Buffalo's pen drive appears as "disk" on my system too. And kingston drives also behave like this. I think the linux driver is unable to find the names of some drives.

---

### Post by markyb86 on 2008-01-23
'disk' is what ubuntu names certain types of drives. the STORE'N'GO drive probably is a fat32 drive with that name, the more pleasant name is what it actually is. If you plug it into windows you can change the name in drive properties, OR if you feel comfortable, you can change the drives names in /etc/fstab

```
gksudo gedit /etc/fstab
```

or kde

```
kdesu kate /etc/fstab
```

---

### Post by mridkash on 2008-02-08
And the solution;
You have to name the volume when formatting it.

How?

use this command to format your pen-drive with FAT 32 filesystem. 
[U]
Warning[/U]: this is a dangerous command, use carefully. Formatting a drive destroys all data on the drive. Do not use sudo in front of command, to be safe.. And make sure you unmount the drive first, by right clicking it and unmount.  In terminal type fdisk -l to see the path of drive

```
mkdosfs -F 32 -n "Pen-Drive" /dev/path/to/drive
```
The -n option gives the volume name to the drive.
After it completes, remove the drive and reinsert it to see a new name.

---

### Post by vanadium on 2008-02-08
You can also provide a label to a fat disk in Ubuntu without having to reformat it (fortunately). See her 
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
to learn how yu can do it for different file systems.

---

