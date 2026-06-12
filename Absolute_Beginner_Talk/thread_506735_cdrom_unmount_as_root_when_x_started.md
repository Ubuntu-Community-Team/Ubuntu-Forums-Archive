---
title: "cdrom unmount as root when x started"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by buzzmandt on 2007-07-22
when x starts or is restarted and i try to unmount/eject cdrom it tells me only root can unmount cdrom, so I open terminal and type sudo umount /dev/cdrom then everything works fine.  I only have to do this once and anytime after that when i open and close the tray it works fine.  but if i have to restart x or restart the comp i have to sudo umount again.

how can i fix this

thanks in advance

---

### Post by Foxmike on 2007-07-24
I thing this is a gnome-volume-manager issue. Acutally, when X is restarted, gnome-volume-manager is initiated to mount your cd before the user is actually logged in, so the user that mounts the cd is root by default. That is why (I suppose) then unmounting the cd becomes an administrator's task.

---

### Post by Skrynesaver on 2007-07-24
In /etc/fstab there are many options which can be given to a filesystem, one of these is user, another is users.  A subtle difference but users allows anyone to unmount a volume and user allows the current user to mount/umount a volume.
[This is a very good guide to fstab]("http://www.openaddict.com/guide_to_understanding_the_fstab_file.html")

---

### Post by Foxmike on 2007-07-24
I didn't know about it, thanks for the link!  I'll sure check out my fstab about that tonight!:)

---

### Post by buzzmandt on 2007-08-03
here is my fstab, > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb7
UUID=11ef3792-32d8-40a5-a5b2-f735360077ec /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F208989D08986281 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=ad4133ab-8684-4f67-83ae-ba5aca5bab9f /media/hdb1     ext3    defaults        0       2
# /dev/hdb6
UUID=91134ee9-343f-42d0-afcf-f02fd90130a2 /media/hdb6     ext3    defaults        0       2
# /dev/hdb5
UUID=0ab5a03c-8d3b-4398-9bdf-59ba60a86d53 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,auto     0       0
OK, looks to me like I need to change the "iso9660 user"> /dev/hdc        /media/cdrom0   udf,iso9660 user,auto     0       0
but what to?


edit, sorry took so long, truck driver here

---

### Post by buzzmandt on 2007-08-03
bump

---

### Post by Inxsible on 2007-08-03
> **buzzmandt said:**
> here is my fstab, 
OK, looks to me like I need to change the "iso9660 user"
but what to?

One thing you could do is to make it ```
iso9660 users
``` note the plural 

> [COLOR=red]users[/COLOR]= when mounted the mount point is owned by the user who mounted the partition and the group users This will work if you are a member of the group in which root is also a member

---

