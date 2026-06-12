---
title: "Access Permissions"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by faixan on 2008-02-11
hi,
i'm having problems with user/owner permissions...
i can read write on my drives, but the problem comes when i try to share folders on my network it says "Access Denied you do not have the permission" but still it opens the sharing tab and shares the whole drive rather than the folder, 
i checked the permissions tab in folder properties it shows...
Owner: root
group : plugdev
text view:drwxrwx---
rest of the options are disabled...
here's my fstab content..
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=aa8764ed-2ba3-4f5a-bf37-936c91eb9d31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ACC3-B354  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=007B-91F1  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=F86D-CE90  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=d75e68f3-1d2a-4914-873e-387e3f654e7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

what should i do?!

---

### Post by dstew on 2008-02-11
Do you want to share your Ubuntu partitions or folders across a local network to a Windows machine?

---

### Post by faixan on 2008-02-11
yes that would be correct.... 
it does share, but not the selected folder but the whole drive which contains that folder and then doesn't let unshare it...

---

### Post by dstew on 2008-02-11
Did you enable Windows networking in System --> Administration --> Shared Folders ?

---

