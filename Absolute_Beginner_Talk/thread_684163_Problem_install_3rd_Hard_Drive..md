---
title: "Problem install 3rd Hard Drive."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by MantinoX on 2008-01-31
Hello Trying to install a third Hard drive  having a little problems.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7168014b-0b81-475c-9c9b-30bc9d5aafa9 /               ext3    defaults,erro$
# /dev/sda5
UUID=216a3322-ebdc-4e94-a216-81400e15151a none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**/dev/hda1       /nas2           ext3    defaults        0       0**


```

```
mantino@mantino-desktop:~$ sudo mount -a
[sudo] password for mantino:
mantino@mantino-desktop:~$ sudo chown -R mantino:mantino /nas2
mantino@mantino-desktop:~$ sudo chmod -R /nas2
chmod: missing operand after `/nas2'
Try `chmod --help' for more information.
mantino@mantino-desktop:~$
```

What did i forget?

---

### Post by PeterJS on 2008-01-31
What are you trying to chmod /nas2 to? You've given it a location, but not the permissions to apply to that location.

---

### Post by MantinoX on 2008-01-31
Im just trying to mount it and get full permission. kinda stumped at the moment, I was following an online source 
[http://www.bradtrupp.com/id/unbuntu-add-hard-drive.html](http://www.bradtrupp.com/id/unbuntu-add-hard-drive.html)

---

### Post by MantinoX on 2008-01-31
What command should i use then?](*,)

---

### Post by PeterJS on 2008-01-31
If you look in the example there, the permissions given are 755, which is full permission for the owner, read and execute for the group, and read and execute for everyone else. Which seems like a reasonable set up, doesn't really matter much on a single user machine as there are no other users to worry about.

---

### Post by MantinoX on 2008-01-31
problem  solved

---

