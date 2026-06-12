---
title: "[SOLVED] Opera flash troubles"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-13
Why in the world am i having so many issues running flash?  Its getting impossible to install..I go to adobe's site and get all the way to 
Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.

/install_flash_player_9_linux/

NOTE: Please exit any browsers you may have running.

Press ENTER to continue...

And i hit Enter (i stored it in my home directory (and created a folder) and it still fails to install after i shut down my browser and restart..any idea why?

---

### Post by Barrucadu on 2008-03-13
It seems to be a problem with the latest version of Opera, as I have had it working in the past. I'm just going to wait for a while until a new version is released.
I very rarely go on sites that require flash, but if I need to, I just switch to Firefox temporarily.

---

### Post by Daveth on 2008-03-13
have you tried the flashplugin-nonfree in the repository? Works in Opera for me, though I'm using the rather unstable 9.50beta.

---

### Post by sports fan Matt on 2008-03-13
Daveth,

Ive been trying with 9.50 Beta and im not sure why its refusing..Am i correctly executing everything?

---

### Post by Daveth on 2008-03-15
have you checked your plug-in directory? Mine is a bit over the top, with 3 flash entries in /usr/lib/opera/plugins, but it seems to work. Falls over at every other opportunity, mind you, but does flash stuff nicely. Can't wait till the full 9.50 release.

---

### Post by forrestcupp on 2008-03-15
You need to enable your backports and proposed repositories, then install the newer version of Flash.

Open Synaptic and go to Settings->Repositories.  Click the Updates tab and check the boxes next to 'Proposed updates' and 'Unsupported updates.'  Then close that window and hit the Reload button in Synaptic.  Then search for flashplugin-nonfree and install it.  That version will work in Opera without any configuring.

---

### Post by Daveth on 2008-03-18
the newer build of Opera 9.5 beta 2 (build 1834) is much better than the previous if as well.

---

### Post by sports fan Matt on 2008-03-19
All is well with flash..Sorry havent been around the last few days to update the issue but there is a newer opera: Version 9.50 Beta 2
Build
1875
Platform
Linux
System
i686, 2.6.22-14-generic
Qt library
3.3.7

At least as of this morning:

---

