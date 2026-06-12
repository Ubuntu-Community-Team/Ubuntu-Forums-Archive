---
title: "&quot;gksudo nautilus&quot; wont work"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by skivan on 2006-04-22
Hi!

I have a FAT32 logical unit that I created during install, I want to use whis drive to share files with my windows computers.

Now to the problem, I cant put anything in it because it belongs to root.

I first created a sub directory called shared with sudo mkdir shared and then tried sudo chmod 777 shared but that did not worked.

I then tried gksudo nautilus and tried to set the permissions but that did not work either.

Anyone who has any ideas??

Thank you.

---

### Post by RRS on 2006-04-22
Edit your fstab line for the partition to:
```
.......vfat iocharset=utf8,umask=000  0  0
```

This will still show root as owner when you right click for properties>permissions but didn't seem to affect my read/write/copy/paste abilities when I had these settings.

You could also use:
```
..........vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0
```

This would change ownership to user (you) but isn't secure, anyone sitting @ your desk would have acess.

Both of the above will also automount the partition @ boot.

[This guide]("http://easylinux.info/wiki/Ubuntu#Windows") should help.

There are probably other options but these worked for me.

---

### Post by Aessu on 2006-04-22
just put chmod 777 /media/(partition here) to the end of the /etc/init.d/rcS.sh if the partition is automounted@boot. if it isn't type sudo gedit /etc/fstab in terminal and add /dev/(partion here) /media/(partition here) vfat noatime 0 0
to the end of the file to automatically mount it @ boot

edit: oops forgot you can't chmod fat partitions... but atleast the mounting part is correct..

---

### Post by aysiu on 2006-04-22
You can't chmod FAT partitions.

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

