---
title: "how to undo a drive installation?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jpl007 on 2007-09-27
I have an external USB harddrive that ubuntu makes read only.  I changed the properties to exec and copied all the other information from the current mount, but now ubuntu reports that it can't mount the drive because of a "/" in the mountpoint.  Where is the mount information for drives stored and how do I 1) correct this issue and 2) make the harddrive writable?

I have a similar problem with the DVDROM as well.  I am trying to install Xilinx software from the DVD, but it won't let me run the executables.  I've tried a root shell to no avail.

THanks much,

---

### Post by justleen on 2007-09-27
mount info is stored in /etc/fstab (but you wont find your usb drive there)

the command "mount" will give you an overview of what is mounted.
"fdisk -l" will show you what drives are avaible.

---

### Post by jpl007 on 2007-09-27
I did look at fstab and mtab, but these seem to be written after the mount.  There is a file somewhere that stores the options the system uses to mount. that's what I'm looking for.  when I plug in the USB drive now, it just reports it can't mount it now.

the other interest thing is that if you just type mount, the list of drives coming back would show the USB drive as RW, but if you clicked the screen icon and then properties it showed the drive as RO (read only)!

:confused:

---

