---
title: "Screen problem iMac 27&quot; ubuntu 10.04"
date: 2010-07-02
forum: Apple Hardware Users
---

### Post by TheJohlin on 2010-07-02
I'm having problems with installing Ubuntu 10.04 as dual boot on my iMac 27".
At first I tried to use boot camp and use that partition for Ubuntu, but when the partition is created and my computer restarts the accessibility icons shows up and then the screen goes black, I hear that the disc is being red so my guess is that the error lies in the display. 

When I tried to boot it without using boot camp and only pressing the C-key at startup, the main menu with installing options shows up, there I pick install ubuntu, obviously, and the screen just goes dark again. Is there something I'm doing wrong?

Thanks in advance!

---

### Post by majortom67 on 2010-07-02
> **heykenen said:**
> When I try to install from CD screen goes black.

iMac 27" i7.

Already postet elsewhere:
----
Same problem here. I've been reading that pressing F6 at the first screen (choose live, install....) will prompt you a menu where you can choose "nomodeset" (if it doesn't work just add the fllowing at the the text line at the bottom: "radeon.modeset=o nomodeset"). The instalation should proceed with standard graphics and let you work in that way for one session. In that session you can download the correct ATI drivers.
Unfortunately for me the problem seems to be elsewhere, in the boot method.

I've been also reading that beta 2 works, UUnfortunately for me, AGAIN, the installer works nice (very very very slow, bythe way) but crashes when I choose the partition to place Kubuntu. I don't know if this is because I have Mac OS X in the first partition, epmty 2nd part for Ext4, empty 3rd partition for SWAp and last partition with Win 7 (which, by the way, may not work anymore).

I'm really bored about all these problems and I'm not sure are related to Apple's hardware.

---

### Post by TheJohlin on 2010-07-02
Thank you! I'll try it!

EDIT: Awesome! It works now!

What problem did you have? The exact same? Which Mac?

---

