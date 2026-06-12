---
title: "cannot access ntfs partition thats mounted as rw"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by addict3d on 2007-02-07
I have an ntfs partition that is mounted as read/write(rw) (When i give the mount command without parameters, it shows the partition is mounted in rw mode).. However, when i do a ls in the directory in which it is mounted as a normal user, it says access is denied.. What do i do ? It allows super-user all kinds of access..

The umask flag in fstab is set to 007 for all partitions, and i dont have issues with other partitions.. Also, this is the first partition (hda1)..

The fstab entry is :

# /dev/hda1 -- converted during upgrade to edgy
UUID=EE240F51240F1C69 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

The output of mount without parameters is :
:~$ mount
/dev/hda5 on / type ext3 (rw,noatime,errors=remount-ro,data=writeback)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda7 on /media/hda7 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda8 on /media/hda8 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda9 on /media/hda9 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
**/dev/hda1 on /media/hda1 type ntfs (rw)**

Thanks for your help :)

---

### Post by bodhi.zazen on 2007-02-07
For rw write access try this :

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

---

### Post by addict3d on 2007-02-07
> **bodhi.zazen said:**
> For rw write access try this :

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)
Thanks for the reply, but the project page link in that link appears to be dead. And i get a 404 for the deb link. Also, is there a way without installing anything extra ? Even read access alone is enough for me

EDIT : Sorry about that.. The project page link is working and i got the deb from that page.. But i would still prefer a way without installing anything even if it allows only read access for normal user.. Thanks again

---

### Post by addict3d on 2007-02-07
I tried that tool and it says there is no such device :shock: .. Am i making some terrible mistake ?? ](*,)

---

### Post by Malta paul on 2007-02-07
Just tried the link at 4:38 GMT and got through twice OK :)

---

### Post by bodhi.zazen on 2007-02-07
> **addict3d said:**
> Thanks for the reply, but the project page link in that link appears to be dead. And i get a 404 for the deb link. Also, is there a way without installing anything extra ? Even read access alone is enough for me

EDIT : Sorry about that.. The project page link is working and i got the deb from that page.. But i would still prefer a way without installing anything even if it allows only read access for normal user.. Thanks again

sorry, it appears the server was down ...

You can not have rw access to your ntfs partitions in Ubuntu without installing something.

You can go with ntfs-3g : [http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)

Or ntfs-config : [http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

Other versions of Linux have these or similar tools pre-installed, but not Ubutnu :(

> I tried that tool and it says there is no such device  .. Am i making some terrible mistake ?? 

Follow the advice in the link I gave you, although it appears the server is down. I will PM the maintainer ...

If you need immediate access use ntfs-3g or Knoppix :)

---

