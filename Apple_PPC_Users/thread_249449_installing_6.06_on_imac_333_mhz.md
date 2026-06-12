---
title: "installing 6.06 on imac 333 mhz"
date: 2006-09-02
forum: Apple PPC Users
---

### Post by macgig on 2006-09-02
cant seem to boot from the cd. or select in startup disk control panel. 

:(

any ideas how to install this? help. 

thanks.

---

### Post by rothgar on 2006-09-02
I have been having the same problem for a while now.  I have not found a solution.  5.10 loaded fine for me but everyithng past that I could never boot on.  I even tried upgrading from 5.10 and everything got messed up.

---

### Post by linear on 2006-09-02
Basic CD booting troubleshooting:

When you're booted in Mac OS, does the CD you have show up on the desktop? It should.

If you hold down the option key right after the chime at startup (with CD inserted) do you get a choice of icons for Mac OS vs. Linux?

If the CD was created from a downloaded iso file, compare the MD5 checksum of the iso file vs. what is posted on the download website. (No match = bad download.)

If the iso is OK, try re-burning at a slow speed (4x or less).

Also check: do you have an Apple keyboard, and is it plugged directly into the iMac? (not into a hub)

---

### Post by 3rdalbum on 2006-09-03
> **linear said:**
> If you hold down the option key right after the chime at startup (with CD inserted) do you get a choice of icons for Mac OS vs. Linux?

You don't on an iMac 333. That feature was added in later iMacs. Also, it's normal for the disk not to be selectable in the Startup Disk control panel.

I don't know what you're doing to try and boot from the CD, and if you're getting an error message or the CD is ignored. Make sure you're holding down the C key from before the computer chimes.

Those early iMacs have problems with their CD drives reading burnt CDs. Try burning at 4x or 8x onto a CD which is specifically made for music. Or, order some CDs through ShipIt.

If you're getting an Open-Firmware error message when you try to boot, that's an incompatibility between Ubuntu 6.06 and a very specific selection of Macs. Ubuntu 5.10 does not have that problem.

---

### Post by bodycoach2 on 2006-09-03
I've loaded Xubuntu 6.06.1 on two G3 (Strawberry and Blueberry) computers. I had to use the 'install' disk, and not the live CD version.

6.06 CD, neither Live or install, would install on the G3. Only when the updated version -6.06.1- was put on the download mirrors was I able to get it to work.

I highly recommend using Xubuntu on the G3 333 Mhz. It's faster than OS 9 was, and way faster than OS X. 

Hold the c key down when booting, and go from there.

> **macgig said:**
> cant seem to boot from the cd. or select in startup disk control panel. 

:(

any ideas how to install this? help. 

thanks.

---

