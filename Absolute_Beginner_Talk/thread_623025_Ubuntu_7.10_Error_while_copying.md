---
title: "Ubuntu 7.10: Error while copying"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by nh.duma on 2007-11-25
I am trying to copy a folder and its contents from Ubuntu 7.10 to an external backup USB hard drive that is formatted with NTFS. The stated reason for the error is that I do not have permission to copy it. Most of the contents of this folder are marked with the "Unreadable" emblem. I have attached an image of the error message. I am able to copy over unlocked files. How do I override the lock on the folder and its contents so that I can copy them over to the backup hard drive?

Thanks,
nh.duma.

---

### Post by jken146 on 2007-11-25
You need read permission for a file to copy that file.  You need to be the owner of that file or acting as root (i.e. with sudo) to change the permission.  

In Nautilus you can right-click on the file > Properties > Permissions and modify the selections accordingly.  To get Nautilus as root hit Alt+F2 and type gksu nautilus

You can change the permissions for multiple files easily enough at the command line.  Use ```
ls -l
``` to list the contents of a folder along with the permissions of each file (in the form rwx(user)rwx(group)rwx)others where r=read, w=write and x=execute).  Use ```
chmod
``` to change the permissions.  For more details see here [http://catcode.com/teachmod/chmod_cmd.html](http://catcode.com/teachmod/chmod_cmd.html)

---

### Post by nh.duma on 2007-11-25
Thanks, jken146. That worked!

> **jken146 said:**
> You need read permission for a file to copy that file.  You need to be the owner of that file or acting as root (i.e. with sudo) to change the permission.  

In Nautilus you can right-click on the file > Properties > Permissions and modify the selections accordingly.  To get Nautilus as root hit Alt+F2 and type gksu nautilus

You can change the permissions for multiple files easily enough at the command line.  Use ```
ls -l
``` to list the contents of a folder along with the permissions of each file (in the form rwx(user)rwx(group)rwx)others where r=read, w=write and x=execute).  Use ```
chmod
``` to change the permissions.  For more details see here [http://catcode.com/teachmod/chmod_cmd.html](http://catcode.com/teachmod/chmod_cmd.html)

---

