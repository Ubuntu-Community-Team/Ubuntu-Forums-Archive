---
title: "NTFS volume in ubutu"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by tibbs.james on 2007-12-23
Hi Guys 

As you can see Im new and i have a question i can't seem to find an answer too.

In Gusty i can view and explore both my windows NTFS partitions this is working all well and good,

What i am hoping to do is to be able to access these partitions without having to enter my Admin password as i find this a real pain. Before anybody suggests to have all my data on a linix partition i run a duel boot and since i already have my files on my windows drive i see no reason to change this when i can already view and write to these drives.

My next question is how can i Map a network drive so i can have an icon on my desktop that takes me to a folder on my other PC across the network

Any help appreciated.

Regards

James

---

### Post by shadow-of-sin on 2007-12-23
What does your /etc/fstab file look like?
Post the output of this command:
```
cat /etc/fstab
```

Also, do you have NTFS-3g installed?

As for your second question, if you already have networking setup, then you should be able to create a link to the folder on your other computer.

---

### Post by tibbs.james on 2007-12-24
> **shadow-of-sin said:**
> What does your /etc/fstab file look like?
Post the output of this command:
```
cat /etc/fstab
```

Also, do you have NTFS-3g installed?

As for your second question, if you already have networking setup, then you should be able to create a link to the folder on your other computer.



For the first bit
james@lappy-386:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f2a06406-b3b2-429a-b319-66652d516919 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=bcd975d6-bb25-4a8b-984e-0c33b3df6031 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


and second question 

I have not specifically installed NTFS-3g

I will try to create a new link but the first time it would not let me

I Get "operation not supported" while trying to create a link from anything over the nerwork

---

### Post by shadow-of-sin on 2007-12-24
Well the easiest way you can get read/write access to your ntfs partition is by installing ntfs-3g. Theres a guide to install it here :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Also, to make a link to networked files on your desktop try creating a mount point for the networked folder and creating a link to that:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by tibbs.james on 2007-12-24
Thanks very Much Appreciate that !

---

