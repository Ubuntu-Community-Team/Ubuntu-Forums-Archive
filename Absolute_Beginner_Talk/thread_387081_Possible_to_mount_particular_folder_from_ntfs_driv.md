---
title: "Possible to mount particular folder from ntfs drive?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by mccartyj on 2007-03-17
I have been able to mount my Windows hard drive in Ubuntu with no problem. However, I would like to mount a particular folder on that drive so that it is more easily accessible.

To be specific, I want to mount the "My Videos" folder to /media/videos instead of having to go through /media/windows then "Documents and Settings", "My Documents", etc. Is it possible to mount a particular folder? Or is there another method to achieve what I am trying to do?

FSTAB:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=53629f8c-68a2-494f-a6f7-02e6b1fc908c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=657a6531-6d38-44c4-bc86-740964324d71 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/floppy1  auto    rw,user,noauto  0       0
/dev/sda1	/media/windows  ntfs    nls=utf8,umask=0222 0 0
/media/windows/Documents\ and\ Settings/Judson\ and\ Jody/My\ Documents/My\ Videos /media/videos ntfs nls=utf8,umask=0222 0 0


That produces the following error: "[mntent]: line 13 in /etc/fstab is bad"

Thanks for your help, and being a great resource for Linux noobs.

---

### Post by newlinux on 2007-03-17
If you've already got your NTFS partition mounted as /media/windows you can create a symbolic link to what you want.

```
 ln -s "/media/windows/Documents and Settings/My Documents/My Videos" /media/videos
```

I think that will work... you must keep you /media/windows/ mount for this to work of course, and modify the first argument to ln -s to be the real path, and the second argument to be wherever you want it linked to.

---

### Post by mccartyj on 2007-03-17
Thanks newlinux! =D> 

That's just what I was looking for. I assume that the link will stay active unless I delete the directory?

---

### Post by newlinux on 2007-03-17
You are correct. Glad that works for you.

---

### Post by Jormanks on 2007-03-18
Could this work in another place instead of /media?
I mean /user/desktop/folder?

---

### Post by newlinux on 2007-03-18
yes, you can create a symbolic link from any folder or file that exists to any other place. Just make sure you have proper permissions to do so in the location where you want to create the link.

---

