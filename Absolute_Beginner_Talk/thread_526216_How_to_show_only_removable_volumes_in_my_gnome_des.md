---
title: "How to show only removable volumes in my gnome desktop?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by heinig on 2007-08-15
I wondering if there is a way to show only removable volumes in the gnome desktop.  Currently I have the option "volumes_visible" set up as true in the gconfig-editor but I couldn't find any option to not show mounted volumes that are not removable (partitions).
Does anyone know how to do that?
Thanks

---

### Post by alex_anthony on 2007-08-15
changing fstab to mount them to /mnt instead of /media should do this

back it up first 

```
cp /etc/fstab /etc/fstab_backup
```

then edit it

```
gksudo gedit /etc/fstab
```

change /media references to /mnt for the partitions you want to hide
then reboot or

```
sudo mount -a
```

to remount to new fstab

externals should still mount to /media and thus show on desktop

---

### Post by Hobo Joe on 2007-08-15
Wouldn't that mess up the functionality?

---

### Post by alex_anthony on 2007-08-15
how do you mean? fstab is only handling the internal partitions. You can mount the internals wherever you want and they are effectively being manually mounted by fstab. the automounting would still be directed to /media

---

### Post by vanadium on 2007-08-15
You are the boss of your system, you organize where your data is stored. Changing the mount point to /mnt indeed will change the location of the data. That may have implications for applications or scripts. These will have to be adapted to look at the new location of the data. Also links to the data will need to be recreated.

---

### Post by vexorian on 2007-08-15
post removal

---

### Post by Hobo Joe on 2007-08-15
I followed those instructions, and now sda1 has dissapeared frm the system, but it says it can't find the disk in my CD drive.

And the last command didn't work.
```

sudo mount -a

```

How can I fix this/restore my backup?

Or could I just change back all the /mnt references to /media?

---

### Post by Inxsible on 2007-08-15
Its not a hard and fast rule, but as a convention, internal drives are always mounted under /mnt and external drives under /media. 

I always use pmount to mount my external drives which mounts them directly under /media
Look at my signature for howto on pmount.

For your internal drives, can you post your fstab and mebbe we can have a look and help you out.

---

### Post by Hobo Joe on 2007-08-15
> **Inxsible said:**
> Its not a hard and fast rule, but as a convention, internal drives are always mounted under /mnt and external drives under /media. 

I always use pmount to mount my external drives which mounts them directly under /media
Look at my signature for howto on pmount.

For your internal drives, can you post your fstab and mebbe we can have a look and help you out.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=67ffe901-e328-4f45-a5c3-2ca25315bc62 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=21bff8f9-90a6-430b-8ee6-dc0232e0f941 /home           ext3    defaults        0       2
# /dev/sda1
UUID=B8E8448FE8444DB6 /mnt/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=3d747e20-d408-41da-a07a-20f7d52b0bf7 none            swap    sw              0       0
/dev/hda        /mnt/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /mnt/floppy0  auto    rw,user,noauto  0       0

```

That's my fstab AFTER the edit. 
Also, like I said the 'sudo mount -a' command didn't work, so that may be part of.

---

### Post by heinig on 2007-08-15
> **alex_anthony said:**
> changing fstab to mount them to /mnt instead of /media should do this

Thanks  alex_anthony, that did the trick!

---

### Post by heinig on 2007-08-15
> **Hobo Joe said:**
> I followed those instructions, and now sda1 has dissapeared frm the system, but it says it can't find the disk in my CD drive.

And the last command didn't work.
```

sudo mount -a

```

How can I fix this/restore my backup?

Or could I just change back all the /mnt references to /media?

Before "sudo mount -a" you have to create the sda1 directory in /mnt ("sudo mkdir sda1").  It worked for me.
If you want to restore your fstab type "sudo cp /etc/fstab_backup /etc/fstab"

PS: I think it's better keep your CD-ROM and Floppy under /media and not /mnt

---

### Post by Hobo Joe on 2007-08-15
> **heinig said:**
> Before "sudo mount -a" you have to create the sda1 directory in /mnt ("sudo mkdir sda1").  It worked for me.
If you want to restore your fstab type "sudo cp /etc/fstab_backup /etc/fstab"

PS: I think it's better keep your CD-ROM and Floppy under /media and not /mnt

I just ended putting it all back to /media, and changing the option in the gconf to hide the drives. This way hides the removable media too, but I don't really mind that.

---

### Post by Inxsible on 2007-08-15
yeah like heinig said, CD Roms are removable media and should be under /media. also creating the folders before you try to mount them helps :)

---

### Post by alex_anthony on 2007-08-16
sorry i forgot to put that in. My fault

---

