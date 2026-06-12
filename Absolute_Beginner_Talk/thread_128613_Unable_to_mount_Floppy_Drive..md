---
title: "Unable to mount Floppy Drive."
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by SumoJim on 2006-02-11
I'm trying to back up data off of an ancient computer by copying into onto a floppy (yes a square one) inserting it into my Linux box and burning it onto a CD. I finally know how to get Ubuntu to burn a CD. But now I'm having trouble getting it to read from a floppy. When I click the "floppy drive" icon I get the following message:

> [SIZE="4"]Unable to mount the selected volume.[/SIZE]

Warning: device /dev/fd0 is already handled by /etc/fstab
supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount.

I have no idea what that means. Can someone help me out?

---

### Post by xx75 on 2006-02-11
Hi SumoJim

Have you mounted your floppy?

If yes then here is a thread I found that might help -
[COLOR="Blue"]*[http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy)*[/COLOR]

I am only a newbie also but I hope this helps
xx75

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=SumoJim]I'm trying to back up data off of an ancient computer by copying into onto a floppy (yes a square one) inserting it into my Linux box and burning it onto a CD. I finally know how to get Ubuntu to burn a CD. But now I'm having trouble getting it to read from a floppy. When I click the "floppy drive" icon I get the following message:



I have no idea what that means. Can someone help me out?[/QUOTE]
Try the following in a terminal:
```

$ gksudo gedit /etc/fstab

```
This should open an editor with some text in it.  Find the line that corresponds to your floppy.  It will look similar to this:
```

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```
Now put a "#" symbol in front of that line, save it, and exit:
```

#/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```
Now you should be able to mount via the GUI or with the pmount command.

---

### Post by SumoJim on 2006-02-11
It seems I've already updated both of the files that were mentioned in that link.. And when I attempted to install pmount I got the message: No packages will be installed,upgraded or removed.... Does anyone else have an idea for me?

---

### Post by SumoJim on 2006-02-11
Awesome cwaldbieser!!! Thats works!!! Thanks a TON!!

By the way? What was I doing when I edited the file?

---

### Post by SumoJim on 2006-02-11
Hmm... Seems to still be a problem with the floppy drive... This time it won't read new information from another disc. And when I try to unmount the volume so I can remount and try again I get the message:

> [SIZE="4"]Unable to unmount the selected volume.
[/SIZE]
unmount:/media/floppy0:device is busy
unmount:/media/floppy0:device is busy
Error: unmount failed

Hopefully the solution isn't to re-boot the computer everytime I need to read from a new disc.

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=SumoJim]Awesome cwaldbieser!!! Thats works!!! Thanks a TON!!

By the way? What was I doing when I edited the file?[/QUOTE]
The (#) is a comment symbol.  You commented out the line.

Ubuntu uses pmount, which is a command for mounting removable media that normal users can use.  It does not work properly with devices that are listed in your file system table (/etc/fstab).  Those entries are for devices that get mounted at boot time.  Also, devices listed there can be mounted with the "mount" command without having to specify the mount point or file system type.

pmount devices should be unmounted with "pumount".  Just like mount, you can't be in the folder when unmounting it or you will get a "file in use" error.

---

