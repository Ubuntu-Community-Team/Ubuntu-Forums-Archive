---
title: "Mountproblem Feisty"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Captaingracekidd on 2007-11-27
Hi, Ive had trouble with not being able to mount Dvds or Cds on my Dell running feisty.
The /etc/fstab shows 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa7a9392-6baf-40d9-87f4-7026c0b74f78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=2317fb1a-bf69-4788-911f-ed6e10d9fba0 /media/sda3     ext3    defaults        0       2
# /dev/sda2
UUID=c1cf5760-c8dc-4973-9135-1022bb5e0517 none            swap    sw              0       0
/dev/dvd       /media/dvdrom0   auto user,noauto     0       0


People in other forum posts has said changing the /dev/dvd could be an issue as well as the auto. But what im wondering is is it really supposed to have the swap listed like this? 
Any help would be appreciated. :)

---

### Post by Shazaam on 2007-11-27
I have two drives, one a cd/rw; the other is a dvd/rw. This is part of my Ubuntu Dapper fstab so it might not help. Dapper doesn't use UUID's but if you search the forum AFAIK you can modify your version. Search the forums to find out before you make any changes.

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by Captaingracekidd on 2007-11-29
I have tried changing my fstab according to all the different tips nothing helps. The thing i did notice is that the under my dvds properties --> permissions - owner : unknown
I cannot change this, not even as root so no wonder it wont mount.

In the fstab though user is listed. 

:confused:

---

