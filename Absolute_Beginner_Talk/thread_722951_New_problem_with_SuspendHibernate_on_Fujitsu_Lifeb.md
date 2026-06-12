---
title: "New problem with Suspend/Hibernate on Fujitsu Lifebook"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by mhaigler on 2008-03-13
I've only recently become an Ubunut, so be kind.  I first installed regular Gutsy, and later changed to Ubuntu Studio 7.10.  In regular-buntu both Suspend and Hibernate worked fine.  But ever since I clean-installed Ubuntu Studio both are broken.  I did download uswsusp, giving me acouple of more options, but to no avail so far.  With the "regular" shutdown methods (clicking the "exit" icon on the desktop) it's as if the "kill-power" signal never gets sent to the computer.  (Remember that this worked fine with regular gutsy, but I did have to manually "brighten" the monitor to get the backlight to come on.)  Here's exactly what happens:

REGULAR SUSPEND (to RAM): Screen fades out, backlight powers off, then back on with a blinking cursor, then imidiately off again,  but then nothing.  The computer NEVER ENTERS POWER-SAVING MODE, and no keys can restore it.

REGULAR HIBERNATE (to disk): Screen fades out, goes blank, backlight goes off, then back on with a blinking cursor, then imidiately off again, then on again with a completely blank screen (no cursor) for about 13 seconds during which time there is a lot of writing to the HD, and then suddenly I'm back at a log-in prompt.  I can log back in fine, and continue, but the system never turns off.

Using s2ram or s2both: screen blanks, and message appears: "looking for splash system... none" and then system freezes with a blinking cursor.  So I guess there's a chance this could work, but there is some sort of issue with the splash screen(?).

I have searched for almost two full weeks on the forums, google, etc., and so far no luck.  Any advice would be most appreciated.  

Thanks,
MH


SYSTEM INFO:
Fujutsu Lifebook P7120D (the tiny laptop)
Running: Ubuntu Studio 7.10, 


mhaigler@FujiTwo:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=d2dc119e-2826-42fd-a413-032e1ae01e49 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=147C4CEB7C4CC966 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=371B33CE5DB03AD8 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
/dev/sda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
mhaigler@FujiTwo:~$ 



mhaigler@FujiTwo:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda3
splash = y
compress = y
early writeout = y
image size = 480328908
RSA key file = /etc/uswsusp.key
shutdown method = platform
mhaigler@FujiTwo:~$

---

### Post by brigid walsh on 2008-04-04
I have the same problem where the computer remains on, though UBUBTU operating system has turned off.  it also doesn't operate the hibernation function.

Have you found an answer?

My computer is a Fujitsu Lifebook 3530.

---

