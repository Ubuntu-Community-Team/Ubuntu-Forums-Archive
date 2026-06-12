---
title: "Installation Problems - X Server Failiure"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by andrew_f on 2007-08-29
Hello,

I am a complete newbie to linux operating systems, but want to give Ubuntu a chance to see if I like it. I intend to set it up on a separate partition on my laptop computer and dual-boot it with my existing Windows XP (not ready to ditch Windows just yet).

***

I downloaded the Live CD and loaded it on boot. First, I tried the top menu option (normal load) and it got to the point where an "X" appears in the centre of a peach background, then a small rotating loading icon, and finally a cursor appears. Then it just hangs until I do a hard restart.

Next, I tried the second menu option (safe graphics) to diagnose the error. When it goes through the loading list, many things do not load, but it continues until it tries to load "GNOME" (the GUI, I presume) and then it fails.

At this point, two things happen:

First, the following error displays itself: "Microcode bcm43xx_microcode5.fw not available or load failed." I am unaware if this is related to the GNOME failure or not but it repeats itself every 15 seconds or so. 

Second, an error box/prompt comes up that says "Failed to start the X server". I choose "yes" to see the detailed report. In that report it says:
> (EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: No screens found.

This, I'm assuming, is the reason the OS didn't fully load in normal mode. From what I can tell, it appears to be an error with the graphics drivers.

***

My laptop is a Gateway MX series model. My graphics card is the stock integrated Intel 82852/82855 family card (or whatever you call it), running at 1280x800, 32-bit.

I've tried looking through the configuration options that you can get to by accessing the "sudo dpkg-reconfigure xserver-xorg" and xorg.config file, but I have no idea what to change, if anything.

Any help is greatly appreciated.

---

### Post by Hobo Joe on 2007-08-29
Use the alternate install CD. There is a choice to pick that on the normal download page.

---

### Post by andrew_f on 2007-08-30
> **Hobo Joe said:**
> Use the alternate install CD. There is a choice to pick that on the normal download page.

Okay, I tried that. Now I have a new, though probably related, problem...

I get through a big chunk of the installer to the point where it attempts to install software (after APT Configuration). When it gets to 6% it attempts to load/install software named "xserver-org" and crashes (deja vu?).

The events happen like this:

1) "Installing xserver-org"
2) "Configuring xserver-org"
3) Black DOS-loading-style screen with flashing cursor (the only time this happens during the installer, probably bad)
4) "Installed xserver-org"
5) "Please wait..."

At that point it hangs.

I don't think my computer and this X Windows System thing get along too well :P

---

### Post by andrew_f on 2007-08-30
Solved. After letting it sit for ~15 minutes it surprised me and kept going.

---

