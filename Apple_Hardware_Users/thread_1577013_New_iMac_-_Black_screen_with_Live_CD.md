---
title: "New iMac - Black screen with Live CD"
date: 2010-09-18
forum: Apple Hardware Users
---

### Post by entangled on 2010-09-18
I'm trying to boot ubuntu10.4 live CD on my new iMac (iMac 11,2, core i3). The screen goes black at start of boot and stays black. The CD stops reading after a few minutes and that's that.

Just to see what else doesn't work I tried ubuntu10.10 beta live DVD. That boots the splash screen - already better than 10.4 - and gives the language menu and the boot option. The boot starts and some text scrolls up the screen quickly. Then the screen goes black, etc.
Tried to set boot option vga=771 - no good. Boot option nomodeset - no good.

Booting suse11.3 live CD also gives scrolling text and a black screen.

All these discs worked on my old Mac Mini Solo (2006).
Looks like something's different about booting a live CD on the new iMacs. Anyone else trying this?

---

### Post by MountainX on 2010-09-19
same problem here.
I have an "iMac11,1" and I'm trying Ubuntu 10.10 beta 32bit

UPDATE: I tried Linux Mint 9 Gnome 32bit - same problem.

> " That boots the splash screen - already better than 10.4 - and gives the language menu and the boot option. The boot starts and some text scrolls up the screen quickly. Then the screen goes black, etc."

---

### Post by MountainX on 2010-09-20
I successfully completed the alternate installer. But when Ubuntu starts up post-install, the screen goes completely black.

---

### Post by linuxway on 2010-09-21
I think its the xorg.conf file that causing that black screen. I had the same problem and it was solved thanks to linuxopjemac.

---

### Post by linuxopjemac on 2010-09-21
I am not very familiar with the Intel machines. You could have a look in /etc/X11. You might find an old xorg.conf file from the GUI installer (not if you used the alternate installer). If you find the older one you can rename it into xorg.conf

---

### Post by MountainX on 2010-09-21
> **linuxopjemac said:**
> I am not very familiar with the Intel machines. You could have a look in /etc/X11. You might find an old xorg.conf file from the GUI installer (not if you used the alternate installer). If you find the older one you can rename it into xorg.conf

Thanks for your reply. I do not have an old xorg.conf file. Maybe I can create one... but for today I will probably just keep using OS X on my iMac.

---

### Post by MountainX on 2010-11-02
Here's the problem. It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

I hooked up an external monitor and booted into a Linux LiveCD and verified that this is indeed the issue I'm having. 

Using options - radeon.modeset=0 nomodeset and installing via the Alt CD do not work around the issue for me. I gave up installing Linux on my particular iMac model.

This issue does not affect all model iMacs. Mine is a 27" late 2009 model.

Here is how to check the serial number to determine the model.

On the bottom of your iMac stand, you'll find a label with the serial number printed on it, or from the Apple menu, choose About This Mac. Configure To Order (CTO) models are designated with an asterisk (*). Check the last three characters on the serial number:
iMac (Mid 2010)
DAS, DNM* iMac (21.5-inch, Mid 2010)
DB7, DNN* iMac (21.5-inch, Mid 2010)
DB6, DNP* iMac (27-inch, Mid 2010)
DB5, DNR* iMac (27-inch, Mid 2010)
iMac (Late 2009)
5PC, B9U, CY8* iMac (21.5-inch, Late 2009)
5PK*, B9S* iMac (21.5-inch, Late 2009)
5PE, 5PJ, CYB* iMac (27-inch, Late 2009)
CYC*, 5PM*, 5RU* iMac (27-inch, Late 2009

---

### Post by slow2anger on 2012-09-22
Hello everyone with the "black screen" issue.  Please take a look at post #23 below.  It might help you.

[http://ubuntuforums.org/showthread.p...ost12255187#23]("http://ubuntuforums.org/showthread.php?p=12255187#post12255187#23")

---

