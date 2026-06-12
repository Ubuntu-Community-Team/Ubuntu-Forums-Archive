---
title: "System freezes up when disconnecting power chord"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by whatYouGet on 2008-03-03
Whenever I disconnect the power chord, the system freezes. If I try to boot with the power chord disconnected, the system will not start up.

I figured I messed something up somewhere, but as a newbie, I don't know where to look. Any help appreciated.

---

### Post by sillyxone on 2008-03-03
try to isolate the problem to hardware/software first by booting up using a Live CD without plugging in.

---

### Post by whatYouGet on 2008-03-03
Thank you for replying!

I have Vista installed on the laptop as well, and I have been doing some test booting to see what works and what doesn't.

Booting into Gutsy with power chord connected.
--Everything OK
--Disconnecting power chord
--System freezes.
--(Turning off, plugging in chord, running fsck, turning off)
Booting into Vista with power chord connected.
--Disconnecting power chord
--Everything OK (Except I'm running Vista, of course).
Booting into Vista with power chord disconnected.
--Everything OK (Except I'm still running Vista)
Booting into Gutsy with power chord disconnected.
--Will not start.
--(Turning off, plugging in chord, running fsck, turning off)
Booting into Gutsy in recovery mode, chord disconnected
--pauses sometimes, resumes booting when I hit the Enter-button
--finally stopping at

* Checking root file system...
fsck 1.40.2 (12-Jul-2007)
^[[B/dev/sda5: clean, 182962/1856832 files, 1508844/3713792 blocks
[ OK ]
* Checking file systems...
fsck 1.40.2 (12-Jul-2007)


By `stopping' i mean blinking cursor for fifteen minutes. This is as far as the system will boot without having the power chord connected.
--(turning off, plugging in chord, running fsck, turning off)

Booting into Live CD with power chord connected
--Everything OK
Booting into Live CD with power chord disconnected
--pauses sometimes, resumes booting when I hit the Enter-button
--Everything OK



So, as far as I reckon this should be a software issue =) I'm wondering what to test for next, though.

Also, I'm getting a warning message for a split second whenever I'm booting into Ubuntu (Live CD as well):

Starting up...
[    13.247616] MP-BIOS bug: 8254 timer not connected to IO-APIC

Wondering how I can fix this?

---

