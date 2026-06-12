---
title: "Help wanted with two Ubuntu Partitions and xorg.conf file"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-06-09
Hi people, god this is embarrassing after helping other people with the same problem ](*,) 
I borked my system.
I have one perfectly normal Dapper install, was ok.
I installed breezy again on a new partition to use for experiments, dapper, edgy etc.

Ubuntu created a new partition at the beginning of the drive and resized and moved my Good Dapper.

When I tried to boot into dapper Grub failed so i reinstalled.

Tried to login again and my xorg.conf decided not to work.

I did the same as I would advise anyone else and did the 
> sudo dpkg-reconfigure xserver-xorg
with practically every combination with and without (nv, nvidia,vesa,DRI,GLX etc)
no go.
Also manual reconfigure
> sudo vim /etc/X11/xorg.conf

I have decided to copy the xorg.conf from the new ubunt install (which is working) into the X11 folder on the other partition.

I need to know how to enable access to the Dapper partition from the New Breezy desktop so that I can transfer/copy-paste the xorg.conf file.

Can anyone provide me with an easy solution ?

Thanks in advance

EDIT : I've got the partition mounted and accessible.
 Thanks to [www.psychocats.net](www.psychocats.net) mount Linux guide
 The only thing is, I can't copy over the xorg.conf file because I don't have permissions.
 Anybody know how to enable the permissions ?

EDIT: Ok forget that as well, found it on Aysiu's website.

---

### Post by richbarna on 2006-06-09
The xorg copy didn't work, and what's more the partition isn't recognised by GRUB.
System completely BORKED !
Complete reinstall coming up !

I will think twice about partitioning, installing a second distro and trusting GRUB.

Anybody else have any problems with an Ubuntu/ Ubuntu Dual-Boot ?

---

