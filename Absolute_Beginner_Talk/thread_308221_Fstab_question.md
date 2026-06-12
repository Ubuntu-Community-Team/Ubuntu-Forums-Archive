---
title: "Fstab question"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-27
Question.  I know how to make a directory for my drive and create a mount point.  My question is how do I exactly know what to put in the last section of FSTAB.

  GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=5c474c3f-0ffb-4b09-aa1a-f1b310159251 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1187a89e-b584-4b85-8772-de04a4b6d230 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

# /dev/hda1 -- converted during upgrade to edgy
UUID=3C5857A0585757AA /windows ntfs nls=utf8,umask=0222 0 0

/dev/hdb1       /media/hdb1     ext3    **_defaults        0       2_**

the options and dump pass section.

I can do all the rest just not sure how you know what to put in that section or if they are always the same.

---

### Post by turbojugend_gr on 2006-11-27
Try "man fstab" in a terminal and read through the manual that appears.

---

### Post by turbojugend_gr on 2006-11-27
Actually ,if you are to lazy to read the man page, 0 and 0 should do it. The first one is set to 0 to indicate no filesystems on that partition are to be dumped, the second one is 0 cause you would likely not want to chack it on start up, if for any reason wish this to be checked on startup for errors, then put 2 as 1 is preserved for the root.

Cheers, TJ.

---

### Post by gentlemanmasher on 2006-11-27
Thanks that clears it up.  Appreciate your help.

---

### Post by bodhi.zazen on 2006-11-27
> **gentlemanmasher said:**
> Question.  I know how to make a directory for my drive and create a mount point.  My question is how do I exactly know what to put in the last section of FSTAB.

the options and dump pass section.

I can do all the rest just not sure how you know what to put in that section or if they are always the same.

**Dump**
Dump: Dump field sets whether the backup utility dump will backup file system. If set to "0" file system ignored, "1" file system is backed up.

**Fsck order**
Fsck: Fsck order is to tell fsck what order to check the file systems, if set to "0" file system is ignored. Root partition should be "1". All others "2" (if you want them checked at boot).

**Defaults section**: Depends on file system and what options you want once mounted:

[color=red]defaults = rw, suid, dev, exec, auto, nouser, and async.[/color]

My recommended options for [color=navy]removable (USB) drives[/color] are in [color=green]green[/color].

[color=red]auto[/color]= mounted at boot
[color=green]noauto[/color]= not mounted at boot

[color=green]user[/color]= when mounted the mount point is owned by the user who mounted the partition
[color=red]users[/color]= when mounted the mount point is owned by the user who mounted the partition and the group users

[color=red]ro[/color]= read only
[color=green]rw[/color]= read/write

(vfat/ntfs) umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
to set permissions of 700, umask=077

(vfat/ntfs) o= Sets owner. Syntax: must use owned **BY USER ID #** not name.
(vfat/ntfs) g= sets group ownership of mount point. Again syntax is by **GROUP ID #** not name.

**_Linux native file systems_**: Use defaults or users. To change ownership and permissions, mount the partition, then use chown and chmod.

Note: Warning re: sync and flash devices:
	[[color=red]_Warning_[/color]](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

Additional Options: (From [wiki.linuxquestions.org/wiki/Fstab](wiki.linuxquestions.org/wiki/Fstab)):

[list]
[*]sync/async - All I/O to the file system should be done (a)synchronously.
[*]auto - The filesystem can be mounted automatically (at bootup, or when mount is passed the -a option). This is really unnecessary as this is the default action of mount -a anyway.
[*]noauto - The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.
[*]dev/nodev - Permit any user to mount the filesystem. This automatically implies noexec
[*]exec / noexec - Permit/Prevent the execution of binaries from the filesystem.
[*]suid/nosuid - Permit/Block the operation of suid, and sgid bits.
[*]ro - Mount read-only.
[*]rw - Mount read-write.
[*]user - Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.
[*]nouser - Only permit root to mount the filesystem. This is also a default setting.
[*]defaults - Use default settings. Equivalent to rw, suid, dev, exec, auto, nouser, async.
[*]_netdev - this is a network device, mount it after bringing up the network. Only valid with fstype nfs.[/list]

---

