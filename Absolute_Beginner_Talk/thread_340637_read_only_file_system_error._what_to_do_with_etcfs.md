---
title: "read only file system error. what to do with etc/fstab? or is that even right?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by kilps on 2007-01-17
Hi all

In the middle of using Ubuntu Edgy under normal use I suddenly began to get 'Read Only File System' errors, when I reboot I get errors regarding duplicate blocks in hda1

From what I have found in the forum so far it has something to do with the etc/fstab file ... which is bellow

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b98f5194-f3aa-49df-bfd0-1e866b91c7f8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5065e0ed-6f9a-49dc-a533-f08b80b15a0f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Is there anything I can do or should I just go the blank installation route? Thanks

---

### Post by jvc26 on 2007-01-17
Your fstab looks the same as mine - can you put up the contents of /etc/mtab?
Il

---

### Post by taurus on 2007-01-17
What file are we talking here?  You can only edit files in your own $HOME directory.  Everything outside of that will give you the read only message since technically only root can modify them.

---

### Post by kilps on 2007-01-17
No no - I got a (specifically) "Read only File System" message when I tried to do anything - including make a new folder on my desktop etc.

mtab:

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=kilping 0 0

```

---

### Post by Buck2348 on 2007-01-17
Hey Taurus:

What exactly is the purpose of the item in the fstab line for the root directory:
```
errors=remount-ro
```  ?
Couldn't that be the source of this problem?

Buck

---

### Post by bodhi.zazen on 2007-01-17
errors=remount ro means if there are disk errors at boot to remount / as a ro file system ....

from man mouint (if that helps):

> errors=continue / errors=remount-ro / errors=panic
    Define the behaviour when an error is encountered. (Either ignore errors and just mark the file system erroneous and continue, or remount the file system read-only, or panic and halt the system.) The default is set in the filesystem superblock, and can be changed using tune2fs( 8 ).

---

### Post by Buck2348 on 2007-01-17
> **bodhi.zazen said:**
> errors=remount ro means if there are disk errors at boot to remount / as a ro file system ....

from man mouint (if that helps):

OK, thanks.  Is that the likely source of the "read-only file system" messages he's getting?

Buck

---

### Post by bodhi.zazen on 2007-01-17
That would be my guess as he is mentioning something about bad blocks at boot.

Perhaps fsck -y /dev/hda1

---

### Post by Buck2348 on 2007-01-17
Kilps:

Have you tried bodhi.zazen's suggestion of running a command:
```
fsck -y /dev/hda1
```
in a terminal?  This would attempt to repair any corruption in your file system that may be causing your trouble.

Buck

---

### Post by bodhi.zazen on 2007-01-17
I should caution you, I am not 100 % on this, and I think you should back up any data first just in case.

also, I think it would be best if you ran that from a live CD with the root partition UNMOUNTED.

This post may also be of assistance:

[http://www.ubuntuforums.org/showpost.php?p=178887&postcount=1](http://www.ubuntuforums.org/showpost.php?p=178887&postcount=1)

As may this:

		[http://www.die.net/doc/linux/man/man8/fsck.8.html](http://www.die.net/doc/linux/man/man8/fsck.8.html)

---

### Post by kilps on 2007-01-18
> **Buck2348 said:**
> Kilps:

Have you tried bodhi.zazen's suggestion of running a command:
```
fsck -y /dev/hda1
```
in a terminal?  This would attempt to repair any corruption in your file system that may be causing your trouble.

Buck
Did that while using the live cd - everthing is working now :D

thanks

---

### Post by wolterkabolter on 2007-08-01
I have the same problem, but I tried fsck -y /dev/hda1 and got the following reply:

```
fsck: fsck.ext: not found
fsck: error 2 while executing fsck.ext for /dev/hda1
```

Can anybody help me out here?

---

### Post by wolterkabolter on 2007-08-01
> **wolterkabolter said:**
> I have the same problem, but I tried fsck -y /dev/hda1 and got the following reply:

```
fsck: fsck.ext: not found
fsck: error 2 while executing fsck.ext for /dev/hda1
```

Can anybody help me out here?

Is there somebody who can help me, or should I give it up?

---

