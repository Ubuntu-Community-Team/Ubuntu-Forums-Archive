---
title: "[SOLVED] No More GUI"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Kymac on 2007-07-28
I have been using a windows/Ubuntu dual boot for a few months now (first time using a non-windows operating system since using macs in elementary school).

Anyway, I decided to install Ubuntu Ultimate 1.4 CD or w/e onto my system, and just format the current two partitions (hence, I'm getting rid of windows all-together).  It took me awhile to get my wireless PCI card to work, however flaky/unreliable (only will be using it for about another month before getting a wired connection anyway).  Anyway, I installed about 70 updates, and did a Ubuntu ultimate upgrade (where I assume it installs a bunch of apps and such, which it seemed to be doing).

Anyway, I reboot my computer, and it goes into the Ubuntu loading screen, and then switches over to a screen with no GUI, no login screen or anything, just white text on a black screen.  I can still login, but there is now GUI.

A screen sometimes pops up that states 'Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?'.

I believe the video drivers had trouble installing or s/t.  So, I was wondering if anyone had a similar problem, and how they fixed it, or would go about finding a solution.  Thank you for reading this.

---

### Post by JAYCEE1 on 2007-07-28
> **Kymac said:**
> I have been using a windows/Ubuntu dual boot for a few months now (first time using a non-windows operating system since using macs in elementary school).

Anyway, I decided to install Ubuntu Ultimate 1.4 CD or w/e onto my system, and just format the current two partitions (hence, I'm getting rid of windows all-together).  It took me awhile to get my wireless PCI card to work, however flaky/unreliable (only will be using it for about another month before getting a wired connection anyway).  Anyway, I installed about 70 updates, and did a Ubuntu ultimate upgrade (where I assume it installs a bunch of apps and such, which it seemed to be doing).

Anyway, I reboot my computer, and it goes into the Ubuntu loading screen, and then switches over to a screen with no GUI, no login screen or anything, just white text on a black screen.  I can still login, but there is now GUI.

A screen sometimes pops up that states 'Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?'.

I believe the video drivers had trouble installing or s/t.  So, I was wondering if anyone had a similar problem, and how they fixed it, or would go about finding a solution.  Thank you for reading this.

startx sometimes works.

Another trick I've used when you get these wierd glitches: pop your live-cd into the drive and boot up on that. Then do an orderly shutdown, eject the live-cd, then try to boot up from HD. Works for me sometimes.

---

### Post by por100pre1 on 2007-07-28
If the previous post doesn't work try logging in and use this command:

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the instructions. When finishing try to start X again:

```
startx
```

Hope this helps.

---

### Post by Kymac on 2007-07-28
Thank You, for whatever reason it didn't work for any of them the first time through, but I tried the ```
sudo dpkg-reconfigure xserver-xorg
``` again, it into the GUI.

Thank You, very much.

[RESOLVED] (hopefully)

---

### Post by por100pre1 on 2007-07-28
You're welcome! I'm glad to help. Now you can mark this thread as solved. :guitar:

---

