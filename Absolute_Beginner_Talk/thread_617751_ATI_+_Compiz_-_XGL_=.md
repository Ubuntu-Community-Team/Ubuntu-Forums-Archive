---
title: "ATI + Compiz - XGL = ?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by hait2 on 2007-11-19
BG Info:

Dell inspiron 6400, ATI mobility radeon x1400

I've had all the fancy compiz effects enabled through the use of xgl-xserver, but that's no longer an option for me because xgl causes a bunch of harmless, yet very annoying problems (see [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130))

Currently, with xgl xserver disabled, i get the "composite extension not available" message as before.

My question is: is there a way to enable compiz effects on an ati card without the use of xserver xgl? Or something not as resource intensive/inefficient that can act as a replacement?

thanks a lot in advance~

---

### Post by hollaburoo on 2007-11-19
If you're willing to try installing the latest fglrx drivers (Which can easily mess up your system), they support AIGLX, which works much better than XGL.

[Fglrx howto]("http://ubuntuforums.org/showthread.php?t=515573&highlight=fglrx")

I understand that Hardy Heron will have these by default though, so you may want to wait for that to be released in April.

---

### Post by hait2 on 2007-11-19
i think i already do have the latest fglrx drivers (they're the proprietary ati ones, right?)
i'll give AIGLX a shot, thanks~

---

