---
title: "mounting ntfs?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-08-27
Okey, so Im pretty new to linux.. been using it a couple of days or so.. I got the ntfs mounted in the first place but then had to reinstall ubuntu because I tried a compiz install wich crashed the whole thing. But I dont remember how I got it mounted and even when I did I didnt get it to stay mounted, I had to remount it after each time I restarted ubuntu. I run ubuntu with gnome btw.

Any help?

---

### Post by geokok1981 on 2006-08-27
The answer u r looking for can be found here.
It is a complete guide for ubuntu and since u r are a new
user make sure to make a bookmark because it
has very useful info.

[http://http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper")

---

### Post by Burnspot on 2006-08-27
Here's a really good guide also:
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by jcrnan on 2006-08-27
okey, so I got it mounted. But how do I keep it from having to be remounted each time I log off?

---

### Post by firebird45331 on 2006-08-27
hope this helps  I don't know if you have ntfs or fat32 but this is what I did.  I had the same problem as you...

[http://www.ubuntuforums.org/showthread.php?t=234493](http://www.ubuntuforums.org/showthread.php?t=234493)

---

### Post by Jayrd on 2006-08-27
> **Burnspot said:**
> Here's a really good guide also:
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

I follwed the instructions, but when I tried to change the permissions I got the message "Couldn't change the permissions of "My Documents" because it is on a read-only disk" 

This is how I set up my fstab settings:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /windows     ntfs    nls=utf8,umask=0222 0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

did I make a mistake?

---

