---
title: "[SOLVED] Basic network printer installation?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-07-04
OK, so I'm so enthralled with Feisty Fawn on my desktop that I just had to install it on my laptop as well!  Everything was great, I figured out how to access files on my WinXP partition, I imported my Quicken data into Moneydance, life is good, UNTIL
I needed to print something to the HP Laserjet 1100 connected to my desktop.
The problem is, when I go to add the printer on my laptop, it's not detected.  And that's where I get lost.  If I choose Network Printer, I have no idea how to fill out the boxes that appear. For example, do I want to install an IPP or CUPS server printer, or a Linux Printer (LPD)?  Or none of the above?  If I opt for IPP, how do I find my URI?  For that matter, WHAT"S a URI?  Sorry to sound like such an imbecile, but this stuff is all Greek to me!  I've been searching for a generic "howto" post, but it seems all printing related posts refer to a specific printer or a specific problem, which doesn't apply to my situation.  I'm probably overlooking something basic.
Here's what I've done so far:
Went to Printer Global settings and enabled "Share Printers"
Edited smb.conf to uncheck the cups-related entries under "Printing"
tried installing network printer using "ipp://WORKGROUP/printers/laserjet-1100" as a URI (no luck there!)
Tried installing the recommended driver "ljet4", but don't know where to look for "PPD Files"

Thanks for any help!

---

### Post by linuxwizard on 2007-07-05
Hope this will help you

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by Speedoo on 2007-07-05
Thanks!
The first link did the trick.  Umm.  Now for another question:
Somehow, while playing with my Samba configuration, I created a printer called "Laserjet", (as opposed to "laserjet-1100" which is the name of my network printer.)  So I went into System-Administration-Printers to remove it, only it won't remove!  Not a big issue, since laserjet-1100 is now resting comfortably beside it, but it seems like I should be able to get rid of the unnecessary icon.  Any tips there?

Thanks again!

---

