---
title: "Help with manual mounting of USB drive"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-10-15
I've got a USB drive which automatically mounts in KDE.  I've now switched to Fluxbox which doesn't automaticly mount this drive and I'm trying to mount it manually.  I've successfully mounted it using:
```
sudo mount /dev/sda1 /media/usbdrive
```

but this mounts with root owner and no group or user permissions.  Any idea how I can mount this as a user or as root with user/group permissions?

I've also tried:
```
sudo mount /dev/sda1 /media/usbdrive -o rw,user
```
but this didn't seem to make any difference.

Finally, this is an NTFS formatted drive.  Any idea how to mount it writable?  Thanks!

---

### Post by Keith_Burton on 2007-10-15
This works for me:
sudo mount -o uid=keith /dev/sda1 /media/usbdrive

Of course, change "keith" to the username you want owning the drive. There's a "gid=" option that works the same way for group.

Note that traditionally, the "-" options come first, before the filenames. However, I tried it the way you did your mount, with the "-o uid=keith" at the end, and it worked. I don't know if that works with every command, though. 

To get write access to NTFS filesystems, look here:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

Keith

---

### Post by anaconda on 2007-10-15
have you checked the rights of /media/usbdrive -directory? 

If you dont have rw rights to that directory then you wont have rw rights to whatever you mount to it, no matter how you do the mounting.

---

### Post by cknight on 2007-10-15
Keith,  Thanks for that.  This did the trick and my usb is now mounting as user owned.  Also appreciated the tip for formatting the command with options.  Next on the hit list is to tackle mounting as writable.

And thanks to anaconda for pointing out that my mounted directory needs to be writable too.  It wasn't and I would definetly have missed this!  Haha I could totally see myself spending hours understanding how to mount NTFS writable, only to forget this minor but important point.

---

### Post by PacketCollision on 2007-10-15
chekc out NTFS-3G.  It offers write suport and is pretty easy to install.

---

