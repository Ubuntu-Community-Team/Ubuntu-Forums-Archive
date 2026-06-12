---
title: "Full Tilt Poker Crashes with Wine"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by setonb on 2007-03-25
I have installed wine, it runs other programs fine, but it won't seem to play nice with Full Tilt Poker.  It always gives me this same error:

wine: Unhandled page fault on read access to 0x0348fe4c at address 0xb7dbb37c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0348fe4c in 32-bit code (0xb7dbb37c).



I am rather new at this whole linux thing, but I'm loving everything that I've seen so far.  The only reason I even need wine is for this poker program.  Any help would be greatly appreciated!

---

### Post by machoo02 on 2007-03-25
Have you checked out [its page]("http://appdb.winehq.org/appview.php?iAppId=2056") at the WINE AppDB?

---

### Post by setonb on 2007-03-25
I have read its page at the AppDB.  I tried doing what they say, even though they don't list my exact problem.  It doesn't seem to be working.   I tried copying the whole folder from a windows installation and it didn't work.  It's always the same thing -- once I log into the server, it connects and I can join rooms, but after about 2 minutes, this same error keeps coming up.  On the AppDB page it lists that the bug that causes Full Tilt to crash has been fixed.  So I assume that means if I'm using the latest version of wine, it should be okay. right?

---

### Post by sloggerkhan on 2007-04-16
Same program on edgy and won't work, either.

---

### Post by YokoZar on 2007-04-16
> **setonb said:**
> I have read its page at the AppDB.  I tried doing what they say, even though they don't list my exact problem.  It doesn't seem to be working.   I tried copying the whole folder from a windows installation and it didn't work.  It's always the same thing -- once I log into the server, it connects and I can join rooms, but after about 2 minutes, this same error keeps coming up.  On the AppDB page it lists that the bug that causes Full Tilt to crash has been fixed.  So I assume that means if I'm using the latest version of wine, it should be okay. right?
So what version of Wine are you using?

dpkg -s wine

---

### Post by setonb on 2007-04-19
This is the version that my computer states I'm using.


Version: 0.9.35~winehq0~ubuntu~6.10-3

---

