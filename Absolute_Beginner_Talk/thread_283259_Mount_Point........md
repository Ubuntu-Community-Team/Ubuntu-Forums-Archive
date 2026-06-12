---
title: "Mount Point.......?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2006-10-23
Can somebody explain to me what is a mount point and what it does...... thanks! ](*,)

---

### Post by woedend on 2006-10-23
a mount point is, in laymans terms, where(as in what directory) you want the device's contents to appear in. 
so if you mounted, say, the cdrom to the mount point /dev/cdrom
when you put in a cd, you could access it by accessing the 'directory' /dev/cdrom.

the mount point must exist, it will not be created for you.

---

### Post by IYY on 2006-10-23
Almost correct, except that /dev/cdrom, and all other files in /dev are not mountpoints but devices. The device /dev/cdrom (which actually links to /dev/hdc) is automatically mounted to /media/cdrom0. Mount points are either in /mnt or /media.

---

### Post by woedend on 2006-10-23
wahaha...damn
mine mounts to /media/cdrom
/dev...oops
bad example i suppose...listen to the smart one ;)

---

### Post by CatKiller on 2006-10-23
[This post]("http://ubuntuforums.org/showpost.php?p=1557220&postcount=10") might help clear it up for you: I was explaining to someone how to change the mount point of a mounted partition.

EDIT: Actually, that post isn't great. I'll leave the link here in case you do find anything of interest in there.

---

