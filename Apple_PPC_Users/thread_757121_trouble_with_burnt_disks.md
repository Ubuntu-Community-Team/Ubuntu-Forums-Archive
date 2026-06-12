---
title: "trouble with burnt disks"
date: 2008-04-16
forum: Apple PPC Users
---

### Post by deamon_knight on 2008-04-16
I just installed Hardy on an Powerbook G3, set to dual boot with OSX 10.3, and most everything works really well. However, I'm looking for help with a snag.

I have CDrs that were created with Nero that will read in my Desktop running Ubunutu 7.10. The disk properly mounts as an audio CD and prompts me to play in the Audio players. However this CD cannot be read in Hardy. This CD can be read in the Mac OS, so I think the problem must be within Ubuntu. Other Pressed CDs mount normally, but the probleam appears to be with burned media. When I insert the CD, Totem Player comes up, but reports "An Error Occurred: Location not found", and no disk is mounted. What can I do to fix this?

Fstab looks like this:
</code>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda11
UUID=562afe1b-6c19-4236-9070-7dc32738abd6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda13
UUID=3a4116ad-8421-4529-b73f-7832cfe28b80 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0

</code>

I'm also not sure how to mount the OSX partition in linux on startup. Any advice?

Thanks!

---

### Post by slacka-vt on 2008-04-16
This is a common problem that I have not found a fix for in any forum.
Nero burns audio cd's as UDF volumes which ppc Linux can not read properly (if at all)
[UDF Problems Ubuntu Thread]("http://ubuntuforums.org/showthread.php?t=616674")
~s

---

### Post by deamon_knight on 2008-04-20
I did find this:
[http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)

However the solution listed there did not work for me. Seems like this is being put off until the the next release?

---

