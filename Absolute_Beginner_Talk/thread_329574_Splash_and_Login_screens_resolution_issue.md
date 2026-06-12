---
title: "Splash and Login screens resolution issue"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by rebartko on 2007-01-01
Hello,

I installed Ubuntu about 15 minutes ago, and I'm a little frustrated right now, so please bear with me if this issue is something that has been resolved hundreds of times already.

When I boot into Ubuntu, the splash and login screens appear all distorted, as if the screen resolution is set incorrectly.  The monitor I'm using with my PC will only support a resolution no higher than 800 by 600; The Mac gets the high-res monitor :) .  When I connect my high-res monitor to my PC, there is no issue, and I am able to login, change the resolution in my user account to 800 by 600, reconnect my low-res monitor, and everything works perfectly ... until I restart and can't login.  I have enabled auto login as a workaround, but I would rather not have this course of action become the permanent fix.  Also, the same issue occurs when I do a live CD boot of both Kubuntu and Xubuntu.  Any suggestions?  Thanks in advance.

Newbie rebartko

---

### Post by MkfIbK7a on 2007-01-01
try going to a terminal applicaitions>acseccories>terminal and typing 
```
dpkg-reconfigure xserver-xorg
```
answer the questions correctly

---

### Post by rebartko on 2007-01-01
Thanks, wert.  Much better.  I now have a login screen, but no splash screen ... and I can live without a splash screen. :)

rebartko

---

### Post by MkfIbK7a on 2007-01-01
> Thanks, wert. Much better.
is this sarcastic?

if you want a splash screen tell me what you are using (e.g. Kubuntu xubuntu ubuntu edubuntu)
and i will find the menu for you

---

### Post by rebartko on 2007-01-14
> **wert613 said:**
> is this sarcastic?

if you want a splash screen tell me what you are using (e.g. Kubuntu xubuntu ubuntu edubuntu)
and i will find the menu for you

No sarcasm at all.  Splash screens aren't nearly as important to me as the user interface.  Thanks!

R.

---

