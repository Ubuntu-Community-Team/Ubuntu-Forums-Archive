---
title: "Unable to start live CD"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Prof.Arronax on 2007-03-11
I have built a new machine with an Intel DG965RY board. Using Core2Duo 2.4GHz/2G (2x 1G) DDR2 ram/1X 250G SATA/2X IDE CD/DVD/PCI Express PX6600 video.  Any Ubuntu (32 or 64 bit) Live CD will start but quits at a prompt saying "bin/sh: can't access tty; Job control turned off".  At this point I am at a BusyBox command prompt; I don't know what to do next.

Some notes that may or may not be of any value: (1) With the 32bit CD, the Ubuntu logo and bouncing progress indicator is normal looking; with the 64bit CD, the initial menu is normal.  Once I select "Start or Install" (on the 64 bit) the display becomes monochrome and the progress indicator is corrupted.  It stops at the same point with the bin/sh: can't access tty prompt. (2) I have updated the motherboard BIOS with the latest platform independent version from Intel. (That made no difference.) (Done from a Win98 bootable flash drive.)

Any suggestions as to what to do next?

---

### Post by HereInOz on 2007-03-11
This may sound silly, and may not work, but, if you have an old PCI video card (S3 Virge or similar)  have a go at replacing your PCIE video card with that old PCI card, and then run the install.  If it works, then the problem is with the video card.

It does look a little like a video problem, and this may at least give you some idea as to where to start.  That card has an ATI chip, I think, and some ATI chips have been known to be difficult.

See how you go.

---

### Post by ConvertOne on 2007-03-11
Have you tried installing from the alternate install CD? In my experience this can solve many problems people have...

James D (ConvertOne)

---

### Post by ajgreeny on 2007-03-11
I think this is a problem related to your DG965RY motherboard.  Have a search on the forum for this and you will find several possible answers to try including this one:-
[http://ubuntuforums.org/showthread.php?t=312436&highlight=DG965RY](http://ubuntuforums.org/showthread.php?t=312436&highlight=DG965RY)

Good luck.

---

