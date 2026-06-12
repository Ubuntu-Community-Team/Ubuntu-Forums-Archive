---
title: "Ubuntu Won't Boot With More Than 1 HDD"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Zante on 2006-11-08
Hey everything!

First off cheers for an excellent distro. I'm slowly moving to Ubuntu but am still a bit rusty on ye' ol' linux commands and stuff.

Well here's my problem,
I have Ubuntu install on a ext3 partition on a SATA drive. That drive also hosts a 40GB NTFS partition for windows. The dual booting works fine with Grub. Now, as soon as I plug in any drive other than the one with Windows and Ubuntu on it the boot sequence in ubuntu freezes and eventually comes up with a weird message.
BusyBox 1.1.3 TTY Can not start control. etc (I can't remember the exact error).
I'm running Ubuntu 6.10.

All other drives are formatted to ext3.

Thanks for any help!

---

### Post by justin whitaker on 2006-11-08
It should recognize the drive and mount it. What are the jumper settings on your other drives, and what does your Fstab look like?

---

### Post by Zante on 2006-11-08
I just turned off all the quiet starts and what not to actually see whats going on. The boot process dies at mounting the drive. It says Warning /dev/sda2 does not exist! Which is odd be because it obviously does lol. Otherwise it wouldn't load with only the sata drive in.

Heres the fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0342222b-ec5c-4017-9532-454cba610b2b /               ext3    defaults,erro$
# /dev/sda5
UUID=d38ab9c0-fa88-42e6-8172-a8f23ee45830 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm stumped for ideas to be honest.

EDIT: I had an idea. When I plug more drives in I'm plugging in a second sata. Maybe the one I'm trying to boot from turns to sdb and the new ones is sda.

---

### Post by gn2 on 2006-11-08
> **Zante said:**
> I just turned off all the quiet starts and what not to actually see whats going on. The boot process dies at mounting the drive. It says Warning /dev/sda2 does not exist! Which is odd be because it obviously does lol. Otherwise it wouldn't load with only the sata drive in.

Heres the fstab:

I'm stumped for ideas to be honest.

EDIT: I had an idea. When I plug more drives in I'm plugging in a second sata. Maybe the one I'm trying to boot from turns to sdb and the new ones is sda.

If you've got two drives you could try this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Zante on 2006-11-09
It was the sata order. By switching the fstab to use the drive location i.e. /dev/sda instead of the UUID number and switching the sata cables around so the second sata is on sdb it boots fine. Yay =D. Now I've just got to set it all up. I hope this has helped anyone with a similar problem.

Also, a tip. If you can get it booting with one drive but not multiple drives try editing grub to actually tell you what's going on instead of just having the splash loader freeze. This is because the error message you get is pretty meaningless. Maybe it's something that could be changed, anyway, it's working yay.

---

