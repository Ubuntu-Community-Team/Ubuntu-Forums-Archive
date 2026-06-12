---
title: "trouble mounting/seeing shared fat32 partitiion in gnome on XP/ubuntu 7.10 dual boot"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by patrick_moore on 2007-12-10
I am relatively new to using Linux/Ubuntu on my own computer, although I feel pretty comfortable with it and consider myself quite computer literate. Last year I installed Ubuntu on an old laptop we had that had some problems that caused us to replace it. I had no problems and enjoyed playing around with it. In the meantime we've replaced that laptop (my wife's), and I have also gotten a new one for myself. (We've recently donated the old laptop to a local group that provides free computers.)

I don't have a particular reason to use Ubuntu other than that I am curious and I have always enjoyed playing around with computers.  

Following (as best I could-- it seemed slightly out of date) the instructions at [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html) , I turned my Gateway MX 6453 laptop into a Windows XP/Ubuntu 7.10 dualboot. 

Everything seems to be working pretty well. 

My only concern is that, following the instructions, I created a shared ( to be shared between wXP and Ubuntu) partition formatted in FAT 32. 

This does not show up as a drive in Gnome, so I assumed it wasn't mounted. So, I poked around a bit and edited fstab a few times (as sudo of course) and in terminal it appears that that partition is mounted. However, it doesn't show up in Gnome, so I'm wondering what use it would be to me until I could get it to do so. My Windows NTFS partition does show up for some reason, as well as the Gateway installed recovery FAT 32 partition. 

Here is what shows up when I type 'mount' at the terminal prompt: 

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hda2 on /media/hda2 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda6 on /share type vfat (rw,noexec,nosuid,nodev,gid=100,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)

/dev/hda6 on /share is supposed to be my shared partition

Here is what my fstab file looks like: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=0d0ca4db-04ce-4d5e-aa08-8279860408e7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=B4A896C4A8968490 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=6A5F-1690  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=475B-F358  /share          vfat     rw,users,gid=users,umask=000, 0       0
# /dev/hda5
UUID=44fe5f59-1940-4f3b-8446-91628d6a7fa6 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

What should I do to resolve this issue? Or, alternatively, is there something fundamental that I am just not understanding properly about this shared partition?

I apologize in advance if I have missed a previously posted solution. I have looked a little on the wiki and have looked at the similarly titled threads the system found for me, and have tried a couple edits to fstab so far, but I still don't see this partition in the Gnome GUI anywhere, even if I go to "Computer" in the file browser. 

Many thanks in advance!

---

### Post by jken146 on 2007-12-11
Which partition are you having trouble seeing?  It looks to me like you have 2 fat32 partitions (hda2 and hda6, both of them mounted, on /media/hda2 and /share respectively).  Browse to these locations and see if you can find the partition you want there.

By the way, things that are mounted in /media should show up by default as desktop icons and in the Places menu.

---

### Post by patrick_moore on 2007-12-11
The partition that I don't see in Gnome is

# /dev/hda6
UUID=475B-F358 /share vfat rw,users,gid=users,umask=000, 0 0

---

### Post by patrick_moore on 2007-12-11
I believe it was fixed. It shows up in "filesystem" as a directory/file folder. I thought it would show up in places/computer/on the desktop as a separate hard drive icon. Thanks again for the help!

---

