---
title: "Problems starting MythTV"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by mikeyandmary on 2007-07-14
Does anyone have an example of the script that allows you to use the power button on a remote to start mythtv??? I have seen heaps of references to such a script but cannot find an example. Everything else is working well.

My setup is DVICO DVB-T USB tuner, Microsoft mceusb2 remote

Thanks heaps...
Michael

---

### Post by mikeyandmary on 2007-07-14
Finally found the script at [http://wilsonet.com/mythtv/tips.php]("http://wilsonet.com/mythtv/tips.php")

Is this script meant to switch mythtv on AND off or just on???

---

### Post by newlinux on 2007-07-14
Looking at the script it looks like on and off (it checks to see if it is running, if it isn't it runs mythfrontend, if it is it kills the mythfrontend process).

---

