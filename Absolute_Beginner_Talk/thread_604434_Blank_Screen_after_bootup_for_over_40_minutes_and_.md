---
title: "Blank Screen after bootup for over 40 minutes and no change"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by megaloyank on 2007-11-06
I asked this question in another thread but now it hasn't been answered for over two days and I'm confused. I was getting really used to using Gutsy for two-three days when this issue happened. I have a HP Pavilion zv6000 laptop with an ATI Radeon Xpress 200M card. It also had the Broadcom 43xx series wireless chipset (BCM 4318 in my case). Fixing the wireless issue using the HOWTO on this thread:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I had to reboot finally and all went well and I booted in fine. However, after shutting down the PC for the night I tried again next morning and now the GRUB loads and I can select my OS choices(dual boot XP). But after a few commands like 'Cannot allocate resources...', the screen goes blank with the backlight on but never boots into the GUI. I left it on for over an hour today and it just didn't reach the login screen. I'm very confused. I'm new to ubuntu and I've no idea what to do. I've the tried the screen resolution HOWTO but I can't make any revisions to usplash in recovery mode using the command line.

Please help!

---

### Post by ajje on 2007-11-06
On startup in Grub press "e" to edit the entry, remove -splash and press "b" to boot.
View the boot-up process for errors and resolve them or post them here...

---

### Post by brianbarry on 2007-11-06
I recently experienced the same problem, my solution was to boot via the troubleshoot menu entry to verify the system wasn't hanging at a particular spot.  At the command line I issued the "login" command.  Once logged in I reconfigured the Xserver to the ati driver, at which time my graphical login worked.  Once logged in via gui I used the restricted drivers manager to reconfigure the Xserver to use the proprietary ati (fglrx) driver and haven't had a problem since.

At the command line issue the following sudo dpkg-reconfigure xserver-xorg and try the ati and not the fglrx driver.

I hope this helps.

Brian

---

### Post by megaloyank on 2007-11-07
That helped a lot. Thanks so much.

However I'm having a different issue now. I have an external monitor connected to my laptop. I disconnected the monitor and changed my screen resolution for my laptop to 1280x800 in the Screens and Graphics option. However, the resolution is not getting applied to 1280x800. I can only keep it at 1024x768 using the Plug n Play option in the monitor detect. If I choose the LCD Panel 1280x800 I don't get an option for 1280x800 in the  dropdown for resolutions.

What should I do?

I have made sure that my graphics card is selected as 'radeon' which is what I have on my laptop.

---

