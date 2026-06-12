---
title: "Absolute newbie questions (fstab + odd gui issues)"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by stormyuk on 2007-01-13
Hi,

I am very new to Linux (1 day!) and ubuntu (using kubuntu distro) and I am struggling alot with it, the first problem is that I can mount my windows drive fine manually but not with fstab.

I followed the instructions I could find yet the drives are not mounting at boot, can someone help?

Here is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d162366d-eb0e-4d80-baa2-56bb74f5083f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=d7a6ab5b-a9a2-41c0-8d80-0b7bc95ca617 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0572feb5-93c1-444f-aebd-8429b0b85c45 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sd1        /media/windows-c         ntfs  nls=utf8,umask=0222 0    0
/dev/sd5        /media/windows-e         ntfs  nls=utf8,umask=0222 0    0
/dev/sd6        /media/windows-f         ntfs  nls=utf8,umask=0222 0    0
```

Here is my fdisk output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       38913   158971207+   f  W95 Ext'd (LBA)
/dev/sda5           19123       29018    79489588+   7  HPFS/NTFS
/dev/sda6           29019       38913    79481556    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            9469        9729     2096482+  82  Linux swap / Solaris
/dev/hda2               1        4734    38025823+  83  Linux
/dev/hda3            4735        9468    38025855   83  Linux

Partition table entries are not in disk order
```

Also I have two quite strange issues with the GUI, one is all my "green" ticks to apply buttons have gone grey yet still work.

The other is the fact, my monitor (Viewsonic LCD) is set for 60hz in KDE which is fine, Yet the login screen seems to insist on using 80hz and looking all blurred as I dont think its supported by the monitor, once the KDE splash screen appears the monitor is ok in 60hz.

](*,) 

Any ideas? Please be gentle :)

Thanks,

Mike

---

### Post by benerivo on 2007-01-13
This is only a guess, but it looks as if the lines for your windows drives in the fstab file may have to read sda1, sda5 and sda6 instead of sd1, sd5 and sd6 as it is at the moment.

---

### Post by riven0 on 2007-01-13
As far as your monitor goes... sounds strange, but have you tried a reconfiguration yet?

---

### Post by bulldog on 2007-01-13
Here's some more info,[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by stormyuk on 2007-01-13
LOL oh dear, I am so blind! Yes, sd# should indeed read sda# !!

Re-monitor, I have reconfigured it in the KDE settings a number of times, would removing the ATI fxgl drivers and retrying installing them help?

I dont understand why all my graphic "accept" buttons etc have all gone grey either, are these issues with the ATI drivers again?

Hmmm, will have a play. 

Is there a way to re-start xwindows after a graphics driver change without having to reboot the PC, as thats getting tedious, its like being in XP again :)

Cheers,

Mike

---

### Post by riven0 on 2007-01-13
> **stormyuk said:**
> Is there a way to re-start xwindows after a graphics driver change without having to reboot the PC, as thats getting tedious, its like being in XP again :)

Cheers,

Mike

You can try doing:

> sudo dpkg-reconfigure -phigh xserver-xorg

and then restart the xserver with: CTRL + ALT +Backspace.

That should be the equivalent of a restart.

---

### Post by stormyuk on 2007-01-14
Hi,

Can I do that with a recover boot? Hehe because now I can't get into Kubuntu at all, it starts to load with the blue bar scrolling, then just gets some currupted horrizontal lines and stops. :(

CTRL - ALT - F* gets nothing, but the numlock on keyboard works so I don't think it can be a hard lock. 

Back in Windows XP for now. :( buuu

EDIT:

Right, back in Kubuntu again, that command worked in recovery, thanks :) The problem is the "green" tick boxes etc still are grey even when they are active, Most bizare :( (not a big problem but niggly as hell).

EDIT (again)

Here is what I mean, when I had changed something before, I could have sworn the "apply" button was with a green tick? Am I going mad?

[[IMG]http://img138.imageshack.us/img138/9586/snapshot1eo8.th.png[/IMG]](http://img138.imageshack.us/my.php?image=snapshot1eo8.png)

Cheers,

Mike (the newb)

---

