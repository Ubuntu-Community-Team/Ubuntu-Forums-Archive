---
title: "[SOLVED] Forcing Screen Resolution"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2008-01-04
Hello all:

Background: [http://ubuntuforums.org/showthread.php?t=658307](http://ubuntuforums.org/showthread.php?t=658307).

So anyway, I got 1680 by 1050 to appear in --> System --> Screens and Graphics and I can switch to that resolution.
However, when I restart the X, or my computer, the default resolution is wrong. It is not 1680 by 1050. In addition, the xorg file reverts back what it was before I added modelines to get the desired resolution. The weird part is that the resolution appears in Screens and Graphics and I can change to it any time, its just annoying and I want Ubuntu to start up with that resolution.

Question: How can I make Ubuntu start with the given resolution 1680 by 1050?


Thanks in advance!

---

### Post by njparton on 2008-01-04
You'll probably need to edit xorg.conf (/etc/X11/xorg.conf) to add this resolution and make it default.

Then reboot or quit gnome and restart gdm and x server.

---

### Post by sirgogo on 2008-01-04
I added the resolution, as shown here: [http://ubuntuforums.org/showthread.php?t=658307](http://ubuntuforums.org/showthread.php?t=658307), but how do I make it default?

Thanks again.

---

### Post by Lostincyberspace on 2008-01-04
> **sirgogo said:**
> I added the resolution, as shown here: [http://ubuntuforums.org/showthread.php?t=658307](http://ubuntuforums.org/showthread.php?t=658307), but how do I make it default?

Thanks again.
Get rid of the others.

---

### Post by LookTJ on 2008-01-04
> **Lostincyberspace said:**
> Get rid of the others.Or you can put it at the top of others in your xorg.conf :)

---

### Post by sirgogo on 2008-01-05
Aiite, so basically this is what I did:

1) Let Ubuntu mess with my settings.
2) Completely uninstall graphics driver.
3) Restart.
4) Select proper monitor information, but keep it at a very low resolution (800*600)
5) Restart.
6) Once everything is low resolution, install graphics driver.
7) Restart system.
8 ) Make sure everything is good (still low resolution), change to higher resolution.
9) Restart the X.
10) Enjoy!

I noticed that simple restarting the X did not fix my monitor problem and did not give me the solution I wanted. I'm not sure why this was, but restarting did the trick.

I'm rockin' now!
Thanks!

---

### Post by zeller on 2008-01-05
Solved then? Have you rebooted since the fix? Still working?

---

### Post by sirgogo on 2008-01-26
Yeah, everything is up and working :).

---

