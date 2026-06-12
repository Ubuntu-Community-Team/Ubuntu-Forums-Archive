---
title: "Display Issues AFTER installation"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by tshearman on 2008-02-18
Moving this to the Newbie forum:

After cruising the forums for a while to figure out how to actually boot to Ubuntu, now once I boot to it the screen blanks out.

System Specs:
Intel Dual Core 2.6GHz
NVIDIA 8800GTS
2 gig Ram
17" HYUNDAI Imagequest LCD Monitor

Also, dual booting between Vista on HD1 (SATA) and Ubuntu on HD2 (SATA).
Everything installed fine; I had no probems with the regular install from LIVE CD.

It appears that it wants to boot; I see "Kernel Live" and something else in the bottom of the screen before the display goes blank.

How do I install ENVY if I cant see anything?

Thanks!

Toby

---

### Post by mikeyphi on 2008-02-19
Try this first:
Boot into Recovery mode - a lot of text which finishes at a Command prompt!
Enter the following:

dpkg-reconfigure xserver-xorg

you will get several pages of text, with a question at the end of each section - accept the defaults unless you know better!

Reboot into normal mode - hopefully you will have a display. You might then need to install video driver via System/Administration/Restricted Drivers Manager
and possible set correct resolution via System/Administration/Screens & Graphics

---

