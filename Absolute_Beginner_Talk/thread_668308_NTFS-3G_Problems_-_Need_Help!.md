---
title: "NTFS-3G Problems - Need Help!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2008-01-15
Hi there, been using Ubuntu now for about a year, been futzing with it for two but I seem to be having troubles with my backup hard drive. I wiped my main drive clean and switched from Dapper over to Feisty in about September of 2007 I would say and I saw that in ADD/Remove it had NTFS-3G available so I loaded it up and set the thing to read/write on my backup and had no troubles till about a month ago. Now I can still read and play everything on it from my music to my pictures but now I cannot seem to write anything to it or delete anything from it. It's like the read part is still there but the write is gone, I get the error message : "Error "I/O error" while copying" msg when I try to copy something to the hard drive or when I try to delete as well. Anyone able to help me fix this at all? Thank you!

---

### Post by justin whitaker on 2008-01-15
> **Tumpster said:**
> Hi there, been using Ubuntu now for about a year, been futzing with it for two but I seem to be having troubles with my backup hard drive. I wiped my main drive clean and switched from Dapper over to Feisty in about September of 2007 I would say and I saw that in ADD/Remove it had NTFS-3G available so I loaded it up and set the thing to read/write on my backup and had no troubles till about a month ago. Now I can still read and play everything on it from my music to my pictures but now I cannot seem to write anything to it or delete anything from it. It's like the read part is still there but the write is gone, I get the error message : "Error "I/O error" while copying" msg when I try to copy something to the hard drive or when I try to delete as well. Anyone able to help me fix this at all? Thank you!

On Gutsy, I had to become root to get R/W going. 

> mount -t ntfs-3g /dev/sda1 /mnt/windows

where /dev/sda1 is the external drive, and /mnt/windows is a directory that you want the drive mounted. 

I have to do the same thing on Mandriva 2008, but Hardy does this natively.

---

### Post by Tumpster on 2008-01-15
> **justin whitaker said:**
> On Gutsy, I had to become root to get R/W going. 



where /dev/sda1 is the external drive, and /mnt/windows is a directory that you want the drive mounted. 

I have to do the same thing on Mandriva 2008, but Hardy does this natively.

Ok so far, but how can I do this to my computer or what can I do to get write working again?

---

### Post by Tumpster on 2008-01-15
Anyone?

---

### Post by warrior24 on 2008-01-15
try 

sudo nautilus 
then find the hard drive then right click select properties
then the permissions tab
change to read and write under your name

---

### Post by Tumpster on 2008-01-15
Initializing gnome-mount extension
** Message: Hit unexpected error "I/O error" while doing a file operation.
** Message: Hit unexpected error "File not found" while doing a file operation.
** Message: Hit unexpected error "File not found" while doing a file operation.
** Message: Hit unexpected error "I/O error" while doing a file operation.
** Message: Hit unexpected error "File not found" while doing a file operation.

Whats all this?

---

### Post by Tumpster on 2008-01-15
Anyone?

---

### Post by Tumpster on 2008-01-16
Bump?

---

### Post by Aurora@FleetBuzz on 2008-01-16
This might help.  It goes into the "hows" and "whys" of mounting partitions and explains the structure of /etc/fstab.  Notice the permissions for each device.  Your problem could be related to this?  I would recommending checking the content of /etc/fstab and see if windows is set to rw.

How to mount filesystems in Linux:
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

How to edit and understand /etc/fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Paulmd on 2008-01-16
> **Tumpster said:**
> Hi there, been using Ubuntu now for about a year, been futzing with it for two but I seem to be having troubles with my backup hard drive. I wiped my main drive clean and switched from Dapper over to Feisty in about September of 2007 I would say and I saw that in ADD/Remove it had NTFS-3G available so I loaded it up and set the thing to read/write on my backup and had no troubles till about a month ago. Now I can still read and play everything on it from my music to my pictures but now I cannot seem to write anything to it or delete anything from it. It's like the read part is still there but the write is gone, I get the error message : "Error "I/O error" while copying" msg when I try to copy something to the hard drive or when I try to delete as well. Anyone able to help me fix this at all? Thank you!

What happened immediately before everything stopped working?

If the answer is absolutely nothing, it may be worthwhile to consider the possibility of a failing hard drive.

---

### Post by Tumpster on 2008-01-16
It's a definate possibility, I do want to get a new one, probably an external 500gb one. That would give me enough to do whatever i wanted with and less wear and tear on the hard drive with it being outside the box. Thanks!

---

### Post by Tumpster on 2008-01-16
This is my fstab, any problems in this at all??
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=39dd682d-a7f8-46a5-8ff9-44e2f64ab658 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=88dff054-1044-4258-850b-7cd0f69b6b8f none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hdb5 /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0

Thanks!

---

### Post by Paulmd on 2008-01-16
> **Tumpster said:**
> This is my fstab, any problems in this at all??
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=39dd682d-a7f8-46a5-8ff9-44e2f64ab658 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=88dff054-1044-4258-850b-7cd0f69b6b8f none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hdb5 /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0

Thanks!

That looks proper, according to the wikipedia article on fstab,

"defaults
    Use default settings. Equivalent to rw,suid,dev,exec,auto,nouser,async."

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

Essentially, the drive IS mounted with read-write access,  You can run programs form it, You have to be root to access it, however.

---

### Post by Aurora@FleetBuzz on 2008-01-16
I take it this is the drive in question?
> /dev/hdb5 /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0

Since it's set for "defaults"as the mount option, I'm not sure if editing would accomplish anything.

I'm afraid I must leave this one for more knowledgeable users to solve.  Sorry.

---

### Post by szaka on 2008-01-16
See [http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror)

---

