---
title: "[SOLVED] brand new dell inspiron bios bug"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-11-17
Hy guys!

I just bought a new laptop, DELL inspiron 1501, it has preinstalled the vista and I wanna get rid of it...
But when I put the ubuntu cd in it, it stops, and displays a bios bug:
..MP-BIOS bug: 8254 timer not connected to IO-APIC
PCI: BIOS BUG #81 [49...] found
PCI: Cannot allocate resource region 7 of bridge 000....

It has a 64 bit processor, but I only have an i386 ubuntu cd on hand, could that be the problem???

Any help would be greatly appreciated, 'cause I don't wanna be stuck with the vista!!!!!

---

### Post by Rinzwind on 2007-11-17
3rd reply in this post:
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

Enter BIOS
disable IOAPIC (for now!).


also read the other replies. There's more sollutions in there.

---

### Post by duruttye on 2007-11-17
well, I tried the solutions there, but they don't work...

I can't find any option or whatever in the bios regarding APIC, and there was a solution of adding the noapic option at startup, but that resulted in another bios bug...

thanx anyway

---

### Post by duruttye on 2007-11-18
Problem almost solved.
Installed ubuntu from the 64 bit cd, work fine, but I can see the error message at boot.

---

