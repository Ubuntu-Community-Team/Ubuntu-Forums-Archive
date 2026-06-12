---
title: "Slow Samba"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by lledurt on 2007-06-26
I am having a problem with my network drives in Ubuntu but not windowsXP

I am running 7.04 and I have a ADS Tech NAS drive kit enclosure with a 300GB drive inside allowing me to share it over the network.  The drive is obviously a Linux kernel running Samba (the instructions even say so)

I mount the folders on the drive with my fstab flie.
# /music user
//192.168.2.101/music    /media/musicusr smbfs  credentials=/root/.smbcredentialsmusicusr,dmask=770,fmask=770,gid=1003  0
# /music reader
//192.168.2.101/music    /media/music smbfs  credentials=/root/.smbcredentialsmusicreader,dmask=750,fmask=750,gid=1009  0
# /familydocs
//192.168.2.101/familydocs    /media/familydocs smbfs  credentials=/root/.smbcredentialsfamilydocs,dmask=770,fmask=770,gid=1011  0
# /picture usr
//192.168.2.101/pictures    /media/pictureusr smbfs  credentials=/root/.smbcredentialspictureusr,dmask=770,fmask=770,gid=1010  0
# /picture reader
//192.168.2.101/pictures    /media/picture smbfs  credentials=/root/.smbcredentialspicturereader,dmask=750,fmask=750,gid=1005  0


often one of the folders doesn't mount (musicusr)
most of the time browsing in nautilus is very slow (60 sec refresh) but konqueror seams faster (initial refresh is slow then browsing is faster)
often ls or cd into my /media is also slow.
on xp the drive is lighting fast

Any suggestions

Thanks P.J.

---

### Post by DugieHowsa on 2007-06-27
I experienced the same headaches myself with smbfs mounts.  You definitely do not want to use smbfs.  You want to use cifs.

Use the post as a guide to configure your mounts for cifs.  Its pretty similar to your existing smbfs configurations.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post should also give you a bit of a chuckle about smbfs:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

---

### Post by lledurt on 2007-07-12
Thanks I will try it.
P.J.

---

