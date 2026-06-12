---
title: "[SOLVED] Gutsy (Kubuntu) won't boot, I think I killed it..."
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-12-31
My laptop has frozen up on me lots of times now and as I don't know how to close it down when it seems to have been totally frozen. I have just held the power button until the screen turned off. That has been fine most times but twice I have got the following message:

> [	19.517002] VFS: Cannot open root device "UUID=36e8826b-5b99-407a-92a0-3d9c70b49348" or unknown-block(0,0)
[	19.517076] Please append a correct "root=" boot option; here are the available partitions:
[	19.517146] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

The first time, it was early in the morning on a bank holiday so I just reinstalled Kubuntu as I had loads of time and nothing to do - obviously I don't want to do it again. How do I get this to install? I have a gutsy live cd if that helps.

Also, as an aside, what am I meant to do when my system freezes? I heard something about typing rseuid or something but I didn't understand it.

Thanks

---

### Post by (((X))) on 2007-12-31
Holding the power button until the screen turn off is no good.
1. Hold down the Alt and SysRq (Print Screen) keys. 2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB 3. Watch your computer reboot magically.

---

### Post by (((X))) on 2007-12-31
How is your laptop frozen? completely or just an application?
If an application like firefox freezes, type xkill in terminal and click on frozen window.
My laptop freezes once a week or so..irritating:confused:

---

