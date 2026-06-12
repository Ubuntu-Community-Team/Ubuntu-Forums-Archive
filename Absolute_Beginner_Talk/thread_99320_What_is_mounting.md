---
title: "What is mounting?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by dpmaxey on 2005-12-05
It says that the pc cannot "mount" the disk volume...which is referring to my Floppy Drive. :confused: I don't know what that is right now. But much information is appreciated.
Thanks. :razz:

---

### Post by KingBahamut on 2005-12-05
To mount a file system (Floppy Drive, Harddrive, CDROM, other such medium)  is to make it ready for use by the operating system, typically by reading certain index data structures from storage into memory ahead of time.

The operating system cannot read the specific medium until it is mounted properly. 

This is typically done via 

sudo mount /dev/<device> /mnt/floppy 

where device is the one associated with your floppy drive.

---

### Post by atoponce on 2005-12-05
As KingBahamut metioned, mounting a volume is giving the operating system to ability to read and write to the volume.  The reasons for this are many, but basically, the main purpose is to swap out storage media without causing harm to the data on that medium, like plugging and unplugging a USB thumb key.  To mount a volume tells the OS that it can safely read and write data.  To unmount a volume tells the OS that no interaction should be allowed between the OS and the drive.

---

### Post by Gray. on 2005-12-05
To find what the device is, type (in terminal):
**cat /etc/fstab**
This should give a table of information and you should be looking for one that looks like:
**/dev/fd0        /media/floppy0**
or similar (those are the ones on my system)
Then try what KingBahamut said using the values you found (/dev/fd0 and /media/floppy0, or similar)

---

