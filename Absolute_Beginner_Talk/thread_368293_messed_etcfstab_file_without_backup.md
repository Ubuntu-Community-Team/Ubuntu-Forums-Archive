---
title: "messed /etc/fstab file without backup"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by nyonga on 2007-02-23
Am a linux newbie, am currently running dual boot with ubuntu 6.10 and windows XP ,  today tried to modified /etc/fstab file to allow read and write on one of my partition. Unfortunately, forgot to back up my old /etc/fstab file. On rebooting,    I see the following:

/etc/rcS.d/S20 checkroot.sh : 407:readlink: permission denied
/etc/rcS.d/S20 checkroot.sh : 407:  usplash_write: permission denied
*cannot initialize /etc/mtab
/etc/rcS.d/S20 checkroot.sh: 407: rm: permission denied
init: unable to execute "/bin/sh" for rc-default : permission denied
init: rc-default (3478) terminated with status 1


how can correct this having to reinstall afresh

---

### Post by Tomosaur on 2007-02-23
If you have a LiveCD, you can boot into that and mount your hard driv. Some editors automatically create backups of files, so it's a possibility that there is one there. It will be called:

```
fstab~

```

If it's not there, you may be able to create a new fstab file.

---

### Post by haricharan on 2007-02-23
you can try installing this software on Win XP... [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html") and this allows u to r/w the linux partitions too...and you can edit the /etc/fstab file from Win XP

---

### Post by nyonga on 2007-02-23
Hi Tomasaur,
thanks for the help, but   am not sure because I recently upgraded from dapper to edgy and  I dont have the live CD for edgy but I have one for dapper, can I use that instead?

---

### Post by nyonga on 2007-02-23
thanks buddy, I have installed the software butb am unable to access the linux partitions. How can I edit  /etc/fstab file/

---

### Post by mykalreborn on 2007-02-23
> How can I edit /etc/fstab file/
[this way]("http://www.ubuntuforums.org/showthread.php?t=283131"). :p

---

### Post by nyonga on 2007-02-23
Thanks man, the link is very great. However, am still not very sure, can this be perform at boot up? Sorry am still new to linux

---

### Post by haricharan on 2007-02-23
after install it you have to goto control panel and select the drives for linux partitions....
i have attached screenshot. if you have anymore questions do tell me....

---

### Post by qoheleth on 2007-02-26
same problem here don't know too much about fstab here is my file here hope someone can help
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=206a6b45-5183-4e21-af73-e17dcaea8abd / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1
UUID=4AE820A8E820946B /media/hda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda5
UUID=a527d99a-e407-4834-a1b9-6bb83b520670 none swap sw 0 0
/dev/hdc /media/cdrom0 auto users,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 <mount\040point> auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 <mount\040point> auto users,atime,auto,rw,dev,exec,suid 0 0
<device> / auto users,noauto,atime,rw,nodev,noexec,nosuid 0 0

---

