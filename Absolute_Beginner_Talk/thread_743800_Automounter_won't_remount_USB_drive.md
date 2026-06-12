---
title: "Automounter won't remount USB drive?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by blue212 on 2008-04-03
I have an external 500GB HDD (WD mybook) and ubuntu 7.10. It doesn't automount after being replugged...

What I do:
I plug the drive in when I am logged in the drive automounts and appears on the desktop.

I right-click and unmount the drive and unplug it from the computer. 

When I plug the drive back in it doesn't automount unless I logout and login again (restart x) 

Is there something that should be refreshing that isn't?

---

### Post by Diabolis on 2008-04-03
I have the same problem. What I do is mount the drive manually.

First make a mount point. You can make it wherever you want, but if you make it inside **/media**, you'll get a icon showing up in your desktop.
```
sudo mkdir /media/usb
```

Change its ownership
```
sudo chown [username] /media/usb
```

Plugin your drive and get its uuid by typing this:
```
blkid
```

Setup the mount point in fstab
```
sudo gedit /etc/fstab
```

Add a line similar to this one depending on your file system:
fat32 file system
```
uuid=xxx	/media/usb	vfat	users,noauto,umask=0000 	0	0
```
ext3 file system
```
UUID=xxx  /media/bootusb   ext3    users,noauto,umask=0000        0       2
```
**You can adjust the entry to your needs, [how to do it]("http://www.tuxfiles.org/linuxhelp/fstab.html")**

Now you can mount the drive by typing
```
mount /media/usb
```

---

