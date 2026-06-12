---
title: "[SOLVED] New dual boot setup - no grub showing up"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-10-19
I just installed 7.10 on laptop with xp.  everything went smoothly.  but when the computer boots up, xp starts and i don't see how to switch to ubuntu. i don't see grub at bootup.  what more needs to be done.  does grub have to be installed separately?  thanks.

---

### Post by Daveth on 2007-10-19
so you are not getting anything that looks like the first graphic on this post???

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by sagesparrow on 2007-10-19
no

---

### Post by stchman on 2007-10-19
> **sagesparrow said:**
> I just installed 7.10 on laptop with xp.  everything went smoothly.  but when the computer boots up, xp starts and i don't see how to switch to ubuntu. i don't see grub at bootup.  what more needs to be done.  does grub have to be installed separately?  thanks.

Question:

Did you install XP after Ubuntu?  If yes then there is your problem.  XP wants to re-write the boot record for its own purposes.

---

### Post by sagesparrow on 2007-10-19
i partitioned a new drive with gparted.
then loaded xp pro, made sure it was working perfectly
then loaded ubuntu today and cannot see grub or figure out how to get to ubuntu

---

### Post by logos34 on 2007-10-19
Do you see anything like "Grub loading..." flash by before it loads windows?   If not then try reinstalling grub to MBR using [this howto]("http://ubuntuforums.org/showthread.php?t=224351").

If that doesn't work see if you can boot ubuntu with [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

---

### Post by sagesparrow on 2007-10-19
i ended up reinstalling ubunut and it worked fine the second time.  thanks.

---

### Post by Arthur Archnix on 2007-10-19
Sounds like the first time you may have installed Grub to somewhere other than the MBR, which would require a few extra steps to get it working, like booting up with a live cd, copying your boot over to your windows partition, then editing your XP bootloader.

Glad your problem is solved though.

---

### Post by Daveth on 2007-10-19
would you please mark your post "solved" then? Makes us all feel so much better:)

---

