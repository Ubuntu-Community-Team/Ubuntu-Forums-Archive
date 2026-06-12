---
title: "mnt versus media directory?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-02-26
I was watching a video on ubuntu linux and they were explaining how mnt and media are both directories that are used in mounting media/drivers.  But there was no explanation on the difference between the two.  I tried doing a quick search in google and there was some information, but I wasn't sure if it's linux specific information or if this information is ubuntu specific.   Just trying to have a better understanding of my system.

Thanks in advance

---

### Post by taurus on 2007-02-26
If you mount something to /media, it will appear as an icon on your desktop so you can access it by double-click it.  Everything mounts to /mnt will not appear on your desktop automatically until you create a short cut for it.

---

### Post by bone2006 on 2007-02-26
thank you so much for the quick reply.  So the only difference is that media creates a shortcut on your desktop automatically?  Seems kind of silly to have two directories for this doesn't it?  Just because one can automatically place shortcuts on your desktop?

---

### Post by taurus on 2007-02-26
The old Unix way is to mount everything to /mnt but since more and more users are running some kind if window manager, they want to have access to their drives directly from their desktop so /media is used.

---

### Post by Zimmer on 2007-02-26
> **bone2006 said:**
> thank you so much for the quick reply.  So the only difference is that media creates a shortcut on your desktop automatically?  Seems kind of silly to have two directories for this doesn't it?  Just because one can automatically place shortcuts on your desktop?
This may help a better understanding of your system for mounting devices
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

and further reading on that site may be of benefit, too...

---

### Post by netkid91 on 2007-02-26
/media is designed for REMOVABLE MEDIA (CD-ROMS, DVD's, USB Drives, etc.).  /mnt dates way back, and has always been used as a temporary directory to mount disks that aren't frequently used.

---

### Post by bodhi.zazen on 2007-02-26
You get various "opinions" re /media and /mnt

Some feel /mnt is used for fixed (hard) drives, and /media for removable devices (cd, usb, etc).

Some feel /mnt is for everything. 

Some feel /media is for everything.

The "standard" is currently /mnt is to be used by sys administrators for temporary mounts.

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html) 

> /mnt : Mount point for a temporarily mounted filesystem
Purpose

This directory is provided so that the system administrator may temporarily mount a filesystem as needed. The content of this directory is a local issue and should not affect the manner in which any program is run.

Of course, there is not universal agreement on this set of standards.

Also pmount uses /media if the devise is not in fstab.

IMO - I use /mnt for hard drives and /media for removable devices. permissions are often different with these devices, so this helps keep 'em straight.

For example, I do not mind if all users have access to removable devices, (permissions 777), but I restrict access to hard drive partitions.

you may use what you like.

HTH

---

### Post by bone2006 on 2007-02-26
I'm not in front of my computer, but if I use ntfs-3g or ntfs-config which seems to automatically select a directory for me, does it automatically select /mnt or does it select /media?

Would it just be easier to have one?

---

