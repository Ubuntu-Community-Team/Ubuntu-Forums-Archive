---
title: "Dual Boot Ubuntu and Vista?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by FLCLFan on 2007-04-19
Hello,

I have 2 hard drives. One with Vista and the other one I'm going to put Ubuntu 7.04 on. And I want to dual boot Vista and Ubuntu. Is there a way i can do this with each OS on a separate HDD? Does 7.04 have a dual boot thing in it?

Thank You!

---

### Post by Doug11 on 2007-04-19
Here you go. This should help.


[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot)

---

### Post by askreet on 2007-04-19
I believe that Vista can be invoked from grub in the same method that Windows XP is:

```

rootnoverify (hdX,Y)
chainloader +1
boot

```

The trick is to install Vista on disk 2 first, then install Ubuntu on Disk 1, and set BIOS to invoke Disk 1 for boot mode.  Ubuntu might even detect an NT OS and add it to your boot menu for ya :)

---

