---
title: "Change the owner of one folder and its files?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-05-07
Beside my “home” folder I have a partition where there is one folder with all my music, and I want to make my user the owner of it. I have tried to open Nautilus as root(gksu nautilus), and right click on the music folder and changed the owner to my user name – but all the folder within the music folder still belong to root :-/ Then I did it again, but tried Ctrl + A then changed the owner to my user, but still the same result... (this worked when I tried KDE, but not now in Ubuntu Feisty with GNOME). 

So, how can I change the owner of that folder and all its files? 

The path to the folder are; /media/sda4/Musikk

Thanks

---

### Post by LaRoza on 2007-05-07
[http://www.linuxheadquarters.com/howto/basic/chown.shtml](http://www.linuxheadquarters.com/howto/basic/chown.shtml)

This is a link to the change owner command.

---

### Post by Cypher on 2007-05-07
Open a terminal with Applications->Accessories->Terminal and type
```

cd /media/sda4
chown -R <username>.<group> Musikk

```
To determine the values for <username> and <group> just go to your home directory and type "ls -l". In most cases both of these is just your username.

---

### Post by _sAm_ on 2007-05-07
Thank you both, I will read the article from that link(I need to learn this, but think it is a bit hard..). 

Edit;
Yes, it worked:) Now I can use the music - thanks again!

---

### Post by NilsE on 2007-05-07
Try to put sudo in front of the command.  This is a root level command so needs the privilege.

---

### Post by Cypher on 2007-05-07
I totally meant to put in "sudo" in my command..honestly I did..;)

---

### Post by _sAm_ on 2007-05-07
I tried, and it worked out just as I wanted - I can now use my music again:-D Have now tried the program called Cowbell for tagging music files and it is just the best! 

Thanks for your help :)

---

### Post by moredhel on 2007-05-07
I don't mean to hiijack this post as I already have mine, but mine says: 

chown: changing ownership of `/media/hdb1': Operation not permitted

after I do:

sudo chown -R (myusername) /media/hdb1

any clues?

---

### Post by Cypher on 2007-05-07
Please show us the output of "mount" and "ls -l /media"

---

### Post by moredhel on 2007-05-07
mount:

```
/dev/hdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /media/hdb1 type vfat (rw,utf8,umask=000)

```

ls -l /media:

```
lrwxrwxrwx  1 root root        6 2007-05-06 23:50 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-05-06 23:50 cdrom0
dr-xr-x---  1 root plugdev  8192 2007-05-06 16:55 hda1
drwxrwxrwx 29 root root    16384 1970-01-01 01:00 hdb1

```

---

### Post by Cypher on 2007-05-07
Ahh it's a "vfat" partition, the ownership info doesn't work the same here as it would with EXT3(Linux) partitions. Your best bet is what you've done, is to set the umask=000 so that anyone can access/create files on that partition..

---

### Post by moredhel on 2007-05-07
ok, thanks :)

---

