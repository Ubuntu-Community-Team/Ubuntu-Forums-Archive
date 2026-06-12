---
title: "One more help  request"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-14
I got all my apps set up finally, but I was wondering, is there a CD Drive emulator for Linux as there is for Windows? If there is please post a link to it, thanks again :)

---

### Post by Xalan on 2007-03-14
[http://www.ubuntuforums.org/showthread.php?t=316093](http://www.ubuntuforums.org/showthread.php?t=316093)

this might help

---

### Post by kpkeerthi on 2007-03-14
You dont want to miss CDEmu. Right here...
[http://www.ubuntuforums.org/showthread.php?t=276743](http://www.ubuntuforums.org/showthread.php?t=276743)

---

### Post by x1a4 on 2007-03-14
Hi,

You don't need an emulator.  Just mount an iso through a loopback device, the way you would a regular file system.  

From a terminal: 

[I]mkdir -p /mount/point
mount -o loop -t iso9660 /path/to/isofile.iso /mount/point[/I]

[*/path/to/isofile.iso* is the full path and file name of the iso]
[*/mount/point* is a directory where you want to mount the file system]

To mount it automatically: 

Edit _/etc/fstab_ to include the iso.  For example: 

**/path/to/isofile.iso /mount/point iso9660 rw,loop=/dev/loop0 0 0**

If you want more ...

[B]/path/to/isofile2.iso /mount/point iso9660 rw,loop=/dev/loop[color=blue]1[/color] 0 0
/path/to/isofile3.iso /mount/point iso9660 rw,loop=/dev/loop[color=blue]2[/color] 0 0
[/B]
... up to the number of loop devices.

---

### Post by Peter1234123 on 2007-03-14
I tried this, it told me that "Only root can do this" but it did not ask me to create a root account, should I log on as [Root] [Password for the account I made]?

---

### Post by jimrz on 2007-03-14
> **Peter1234123 said:**
> I tried this, it told me that "Only root can do this" but it did not ask me to create a root account, should I log on as [Root] [Password for the account I made]?

no need for all of that...just type "sudo " before each of the commands described, then enter your user password when asked. this will give you root priviledges for that command

---

### Post by aysiu on 2007-03-14
```
sudo nano -B /etc/fstab
``` allows you to edit the /etc/fstab file with root privileges.

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

