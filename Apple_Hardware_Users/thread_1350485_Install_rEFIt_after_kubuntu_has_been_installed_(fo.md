---
title: "Install rEFIt after kubuntu has been installed (for dual boot)"
date: 2009-12-09
forum: Apple Hardware Users
---

### Post by skore on 2009-12-09
So for some strange reason I've managed to install kubuntu for dual-boot with OSX without using rEFIt - and now I run into problems (of the OSX kernel panic kind) when starting OSX.

Is there a way to install it now?

---

### Post by skore on 2009-12-09
What I have already tried:

- Install rEFIt from the kubuntu live cd (didn't get anywhere with that - wasn't found in any repository)
- Write the rEFIt boot cd in k3b (doesn't recognize the image - so I forced ISO writing)
- Also tried forced ISO with Mode1 or Mode2 forced

All three Boot CDs don't do anything on startup (kubuntu one works - so I DO know how to make one ;) ).

Right now I'm trying option F: Banging my head on the table until it works - anybody got a better idea?

Edit: It would already be a great help if somebody had a working rEFIt CD and could make an .iso image from that (it should only be a couple of MBs) - I have the strange feeling it is k3b failing on me here...

---

### Post by skore on 2009-12-09
Adding in the readout of the kernel panic, so this topic is more searchable for other people:

panic(cpu 0 caller 0x2ad0d5): "Incompatible boot args version 1 revision 4\n"@/SourceCache/xnu/xnu-1486.2.11/osfmk/i386/AT386/model_dep.c:542
Debugger called: <panic>
Backtrace (CPU 0), Frame : Return Address (4 potential args on stack)
0x10be78 : 0x21b2bd (0x5cf868 0x10beac 0x223719 0x0)
0x10bec8 : 0x2ad0d5 (0x592af4 0x1 0x4 0x82e66000)
0x10bf38 : 0x61bf4d (0x5879eb 0x8221a8 0x4 0x61bb6f)
0x10bf68 : 0x2ad609 (0x592cef 0x10bf8c 0x4 0x61c483)
0x10bf98 : 0x297739 (0x1 0x209e488 0x4 0x209e488)
0x10bfe8 : 0x29e93b (0x209e488 0x0 0x29e911 0xcb000008)

BSD process name corresponding to current thread: Unknown

Mac OS version:
Not yet set

Kernel Version:
Darwin Kernel Version 10.2.0: Tue Nov 3 10:37:10 PST 2009; root:xnu-1486.2.11~1/RELEASE_I386

System uptime in nanoseconds: 0

---

### Post by skore on 2009-12-09
Btw - I can boot using [this trick]("http://ubuntuforums.org/showthread.php?t=1319037&highlight=Incompatible+boot+args+version+revision") (holding left alt key on startup) - so OSX itself is not the problem here.

---

### Post by buntuLo on 2009-12-09
are you trying to boot from the rEFIt cd holding down the 'c' key, as i suppose you did for the (k)ubuntu livecd?

---

