---
title: "Xserver not starting?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by KoRnholio on 2006-07-10
I installed Breezy fine, on a dual-boot with XP, and it was working fine.  I even installed the Easy Ubuntu packages without a problem.

Then I logged into Windows, essentially did nothing, and restarted again, to log into Ubuntu.

At Grub, I select the latest Ubuntu version, and it successfully reaches and passes the loading screen (the ugly black and brown one, which lists all the things its doing as its starting up).  However, after then, nothing loads.  The blank screen (with the blinking cursor) comes up, the blinking cursor goes away, and nothing happens.

It appears that the system is loading fine but the X server is hanging for some reason.  Doesn't give me any error messages.

It passed installation fine and I was in the X server then for a while, without any problems.  It was only on this reboot.

Would i have to reconfigure the X server?  Or does this problem sound like something else?

---

### Post by trent dillman on 2006-07-13
Try rebooting in rescue mode. If you get a root shell, it's probably X.

---

