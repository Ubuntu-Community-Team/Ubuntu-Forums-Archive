---
title: "Can't get wireless to work"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by buddydough on 2007-03-05
Ok, I am new to this op system, and I can't get any of the startup disk to work for my Linksys Wireless-G USB Network Adapter with Speed Booster.  Wine opens up and says "cannot open .\License_En.rtf."  Also, this is what happens in the konsole.  buddydough@loved:~$ wine /media/cdrecorder/Setup.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub.

If anyone could help solve the problem that would be appreciated.  Thank-You

---

### Post by sunexplodes on 2007-03-05
I don't have the time right now to run through this in depth, but you'll most likely need to use an application called NDISWrapper to use your windows drivers with Ubuntu. Do a search in the howto section of this forum for ndiswrapper, and you'll come up with a variety of instructions that are probably better than what i could provide.

Good luck!

---

