---
title: "Previously writable partition is now Read-Only."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-10-15
Hello,

I have a partition that's been writable for several months now, and suddenly, it's read-only.  I have no clue what may have caused this.

When I go to System -> Administration -> Disks, all the boxes are checked for this volume (it's readable, writable and executable by everyone, just as I set it to be), so it's showing that all's well, but it really isn't.

The partition is purposely FAT-formatted, so it can also be used by Windows.  This is where I keep my Ubuntu-Windows shared files (photos, financial docs, and Firefox config files).  As far as I know, I've done nothing in Ubuntu or Windows to cause this (and indeed, I've only been to Windows once in the last month or so, to see if this problem was fixable from there).

Any idea how I can restore the partition to its writable state?

Thanks for any help you may have!

-Mark

---

### Post by taurus on 2006-10-15
If you mount that partition at boot, then past your /etc/fstab here...

```
more /etc/fstab
```

---

### Post by mjpatey on 2006-10-15
When you say to mount it at boot, do you just mean to let it mount automatically as it usually does, or something more?

Thanks,

-Mark

---

### Post by taurus on 2006-10-15
> **mjpatey said:**
> When you say to mount it at boot, do you just mean to let it mount automatically as it usually does, or something more?

Thanks,

-Mark
I mean that when you boot up, everything is already there for you to use UNLESS you mount that partition by hand, typing in the command from a terminal!!!  Either way, a quick look at your /etc/fstab would be good!

---

### Post by bbukh on 2006-10-15
Check your system log. When there is an error writing to the disk, the kernel switches the filesystem to read-only. If the system log is on the other harddrive than the harddrive that failed you will see the errors in the log. Check whether you had any harddrive failure recently. For example, use smartmontools to read the record of the past performance of your harddrive (see [http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983) for introduction).

-Boris

---

### Post by mjpatey on 2006-10-15
Thanks, everyone... I'll post my fstab output as soon as I get home to my Ubuntu box (sorry, I'm at work, where all we gets is Winders!)  Should be in about 2 hours.

Boris, thanks for the insight.  Assuming all's well in fstab, I'll check that out.

-Mark

---

### Post by mjpatey on 2006-10-16
Taurus, here's what I got:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb3   /media/share   vfat   defaults,umask=000

... and the partition in question is hdb3.

Thanks!

-Mark

---

### Post by taurus on 2006-10-16
> **mjpatey said:**
> Taurus, here's what I got:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb3   /media/share   vfat   defaults,umask=000

... and the partition in question is hdb3.

Thanks!

-Mark

Okay, try something like this for the last line in your /etc/fstab...

```

/dev/hdb3   /media/share   vfat   defaults,umask=0000   0   0

```
Reboot and see if you can write to /media/share again.

---

### Post by mjpatey on 2006-10-16
I changed the line, but it seems to have had no effect... it's still read-only.

---

### Post by dannyboy79 on 2006-10-16
well, after you did that, you would need to make sure you unmounted it and then remounted it to ensure that the changes take effect. that would be done by
sudo umount /dev/hdb3
and then 
sudo mount -a
then see if that did anything. if not, try to make like this

/dev/hdb3 /media/share vfat rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0

that's what mine looks like and i don't have any issues. the uid and gid are the user id and group id and most ubuntu installations make the first user and group 1000.

---

### Post by jorn on 2006-10-16
This is what my fstab says:
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
It's taken from here:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by mjpatey on 2006-10-16
I just tried Dannyboy's suggestion (changed my hdb3 line in fstab to read as his does), then rebooted... and just to be sure, I unmounted and remounted. Unfortunately, it's had no effect.  Still read-only.

---

### Post by dannyboy79 on 2006-10-16
can you write to it in windows?

---

### Post by mjpatey on 2006-10-16
I have a very interesting answer to your question, dannyboy79...

I just booted into Windows to see if it could write to it, and Windows automatically went into its light-blue "something's wrong with one of your disks" mode where it checks file consistency before booting.

It found 2 files on that partition that had become corrupt, and then truncated them.  I then was able to write to the drive from within Windows, and now just tested and Ubuntu writes to it just fine, too!

This is the second time I've had a problem with a file getting corrupted on that partition, and both times, rebooting into Windows seemed to solve the problem.  There must be something I could have done in Ubuntu to solve this problem, but so far I don't know what.

Now, it very well may be that Windows caused the problem, and therefore it knows how to fix it.  I don't know anything about this stuff.

Does anybody know what I would do to determine if I have a corrupt file in Ubuntu?  Windows found it and nailed it automatically, but I have to think that there's at least a way to find this stuff in Ubuntu and squash it manually.

I know I have over 180 "beans" here, but I'm still very new to the technical aspects of Ubuntu and Linux in general.  Please excuse any seemingly (or actually) idiotic presuppositions I may make.

Thanks for any info you may have.

-Mark

---

