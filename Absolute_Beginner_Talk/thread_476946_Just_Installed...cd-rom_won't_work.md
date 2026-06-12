---
title: "Just Installed...cd-rom won't work"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by johnymac81 on 2007-06-17
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=450231](http://ubuntuforums.org/showthread.php?t=450231) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I just installed Ubuntu....this is my first time using Linx.  So far, I have been able to get everything to work except the my cd-rom.  When I insert a cd-rom nothing happens...when I click on it...I get the message "unable to mount media."  The cd-rom will read the Umbuntu cd when I start...so I don't think its a hardware problem.  

I really don't know anything about Linx, so please be very specific if you are kind enough to respond.  I found other people in the forums who had similar problems, but I didn't see a resolution.
desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=85c74f98-0435-4f3f-b34a-0148cbdc2681 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d6053aa0-7038-49b8-bf8e-8122e07cab5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
desktop:~$ ls -al /dev/cdrom*
lrwxrwxrwx 1 root root 4 2007-06-17 19:38 /dev/cdrom -> scd0
-desktop:~$ ls -al /media
total 20
drwxr-xr-x  5 root root 4096 2007-06-17 19:38 .
drwxr-xr-x 21 root root 4096 2007-06-17 16:49 ..
lrwxrwxrwx  1 root root    6 2007-06-17 10:36 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-06-17 10:36 cdrom0
drwxr-xr-x  2 root root 4096 2007-06-17 10:36 cdrom1
lrwxrwxrwx  1 root root    7 2007-06-17 10:36 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-06-17 10:36 floppy0
-rw-r--r--  1 root root    0 2007-06-17 19:38 .hal-mtab
--wxr-x---  1 root root    0 2007-04-15 07:56 .hal-mtab-lock

---

### Post by johnymac81 on 2007-06-17
Update:

I just tried my second cd-rom drive...and that drive works...but anyway I can get the first one to work too?

---

### Post by johnymac81 on 2007-06-18
anyone?

---

