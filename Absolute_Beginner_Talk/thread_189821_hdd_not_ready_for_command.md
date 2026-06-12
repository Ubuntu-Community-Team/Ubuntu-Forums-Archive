---
title: "hdd not ready for command"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2006-06-05
Recently I have been having a small problem where bootup takes unusually long at the point 'mounting root file system' (takes about 40 seconds to progress beyond this point).

I have :
Primary master 80Gb IDE drive (hda)
Secondary master 80Gb IDE drive (hdc)
Secondary slave is Sony DVDRW IDE drive (hdd)

Ubuntu Dapper is on Secondary Master (hdc4)

What I have found is that by removing the 'splash' entry in /boot/grub/menu.lst, the now visible error I get is as follows (appears after the 40 sec delay) and appears twice.
> hdd not ready for command

What I have found is that by removing the DVD drive completely, this delay is reduced to almost zero.

Bootup is normal otherwise.

Any tips as to what might be happening here?

> Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

---

### Post by falcon15500 on 2006-06-22
Hi... Sorry for not replying sooner.  From the description given, its possible that there is a bootup attempt to configure your DVD drive with **hdparm**.  This may be resulting in the error message you are getting.  Obviously removing the drive completely solves this.

  I would suggest having a look through your startup scripts to determine if this is the case.  If you can find a point where hdparm is being used on your DVD drive, try commenting it out and reboot to see if it has any effect.

falc

**Edit:** Just looking through my own /etc/init.d and there is a hdparm script.  There is a comment in the script that alludes to a "nohdparm" option.  You can add nohdparm to your kernel options line in your grun menu.lst and hdparm will be skipped for that boot.  Obviously, this will probably slow all your normal disk operations - but its a quick way of confirming if this is where the problem lies.

---

