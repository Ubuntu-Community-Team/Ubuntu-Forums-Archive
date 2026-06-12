---
title: "[SOLVED] Strange /etc/fstab entries (Solved)"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-10-30
Hello all,
I installed Ubuntu 6.10 from scratch. There were no errors during installation. I wanted to install LiLo for dual boot purposes and when I wanted to configure LiLo with "sudo liloconfig" I got this message:
 
> root@BitByter:~# sudo liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.
    
    WARNING!
        Your /etc/fstab configuration file gives device UUID=53f0d353-de24-48ca-a30a-6b383787e215 as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle. 

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

I do not have a RAID array and at the time of installation I had only one hard drive installed.

I checked /etc/fstab: 
root@BitByter:~# vi /etc/fstab 
and here is what I found:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=53f0d353-de24-48ca-a30a-6b383787e215 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=c94296a5-55c5-4962-a325-adf5879dea98 /Storage        ext3    defaults        0       2
# /dev/sda2
UUID=70377f65-09c1-4c9b-9a47-09863850aa1d /boot           ext3    defaults        0       2
# /dev/sda5
UUID=e545da91-3ba4-4c52-a604-3626bf37a94f /home           ext3    defaults        0       2
# /dev/sda6
UUID=df6a1262-5620-400a-ad81-ab7e4d0b20de /usr            ext3    defaults        0       2
# /dev/sda7
UUID=24068134-e03a-42cd-b17e-9dadbb62e2e8 /var            ext3    defaults        0       2
# /dev/sda8
UUID=81a41363-ffc9-4d52-bb6b-cee70f3f29a1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/             /media/floppy0  auto    rw,user,noauto           0       0


[COLOR="Blue"]Please, can one explain me what to do with all these UUID= lines, which I never had before in any Linux installations?[/COLOR]

---

### Post by aysiu on 2006-10-30
I think they're just different ways to refer to what's in comments.

Try substituting ```
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
``` for ```
UUID=53f0d353-de24-48ca-a30a-6b383787e215 / ext3 defaults,errors=remount-ro 0 1
```

---

### Post by bodhi.zazen on 2006-10-30
Fstab seems mysterious to many Linux users.

If you are interested I wrote a short explanation of fstab which covers this issue as well as an intro to fstab:

[[color=navy]Understanding fstab[/color]](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Cariboo1938 on 2006-10-31
> **aysiu said:**
> .....
Try substituting ```
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
``` for ```
UUID=53f0d353-de24-48ca-a30a-6b383787e215 / ext3 defaults,errors=remount-ro 0 1
```Thanks,aysiu, that helped. Now I can run liloconfig. The only problem is that I do not want to install LILO on sda1 (which is the  / partition) , as suggested in the config dialog, but on sda2 (which is the /boot partition). The reason is because I thought GRUB is in the MBR, which is on sda1 and there can be not a second boot loader on the same partition. 
[COLOR="Blue"]How can I install LILO on sda2? Or am I thinking incorrectly?[/COLOR]

---

### Post by Cariboo1938 on 2006-10-31
> **bodhi.zazen said:**
> Fstab seems mysterious to many Linux users.
If you are interested I wrote a short explanation of fstab which covers this issue as well as an intro to fstab:
[[color=navy]Understanding fstab[/color]](http://ubuntuforums.org/showthread.php?t=283131)This is a very interesting theme! Great work! Thank you, bodhi.zazen!;)  
(Actually I need more time to understand it and I have to read it a few times. Thanks for showing me what is behind the fstab. To me right now it seem to be complicated and I asked myself has it to be that complicated?)

---

### Post by Cariboo1938 on 2006-10-31
> **Cariboo1938 said:**
> Thanks,aysiu, that helped. Now I can run liloconfig. The only problem is that I do not want to install LILO on sda1 (which is the  / partition) , as suggested in the config dialog, but on sda2 (which is the /boot partition).
[COLOR="Blue"]How can I install LILO on sda2? Or am I thinking incorrectly?[/COLOR]
Yeah...Problem solved! I changed the partitions. Using the live CD and Install menu, I repartioned sda1 to "/boot" (there is MBR installed) and sda2 is now "/" (here I could install LILO). Now I could create a GAG46 Boot Floppy!
Thanks everybody.:D

---

### Post by amoore on 2007-02-07
I need to try this

---

