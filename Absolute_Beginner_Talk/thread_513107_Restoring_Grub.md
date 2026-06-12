---
title: "Restoring Grub"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Dr Zolygon on 2007-07-30
Hi,

   I installed window after i installed ubuntu 7.04 and now my grub menu is gone. I know a little about how to restore grub but im a noob and am having trouble figuring out which drive to save it to(such as hd 0,0). What is the command to find out what the name of the drive i want? And how do I get windows xp to show up on the list?

Thanks.

---

### Post by ramjet_1953 on 2007-07-30
All you need to do is to download the [COLOR="Blue"]Super Grub Disk[/COLOR].

It is a self-booting iso that you burn to a CD.

It is great at fixing up GRUB issues.

You can download the iso from here: 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Regards,
Roger :cool:

---

### Post by Famicommie on 2007-07-30
[Recovering Ubuntu after installation of Windows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

That link is a nice step-by-step guide.

---

### Post by MQMike on 2007-07-30
Those are excellent references.
Here's another one( that I wrote):

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

This easy to fix.  Windows overwrote the GRUB bootloader on the Master Boot Record.  You just need to re-install GRUB to the MBR which is called (hd0).
The part to watch for (in the How-To's) is
root (hdx, y)
setup (hd0)
quit

all done at a GRUB prompt, grub>.

---

### Post by MQMike on 2007-07-30
You're not alone . . .

[http://ubuntuforums.org/showthread.php?t=513151](http://ubuntuforums.org/showthread.php?t=513151)

---

