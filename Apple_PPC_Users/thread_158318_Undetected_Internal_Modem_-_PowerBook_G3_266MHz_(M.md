---
title: "Undetected Internal Modem - PowerBook G3 266MHz (M4753)"
date: 2006-04-10
forum: Apple PPC Users
---

### Post by Matthewb57 on 2006-04-10
Hey,

I've been searching for solutions all over the net with little results.  I'm getting a little frustrated with trying to find a solution.  I've used some different linux distros, and played with a lot of different hardware setups for some time now, but mainly on x86 architecture.  This is the first time on a Mac, and an old one at that.

I have a PowerBook G3 266MHz (Family M4753), codenamed "Wallstreet" I believe.  My problem is that the modem was not detected during the kubuntu install.  It's not that big of a deal, but it would be nice to have a working modem for faxing purposes.  Anybody know what modem is actually in this thing?  From some specs, I believe its a 56k, but I have no idea what chipset, etc.  I just need to find a driver I guess, but I don't know where to look.

Anybody know of a good place to start looking for this stuff?  Everything else seems okay on the laptop.  Sound works, network works, video seems fine.  I just can't get that modem going.  Any help is appreciated.

I've searched the forums, not much came up, so sorry if this has been answered already.

Thanks for helping out,
Matt

---

### Post by towsonu2003 on 2006-04-14
not sure if it applies to PPCs but, have a look at second link in my signature...

---

### Post by Matthewb57 on 2006-04-16
Turns out the modem was a serial modem and was controlled through ttyS2.  I installed Minicom and switched ttyS? until I found it to be ttyS2.  Thanks for the info about the modem wiki.  I believe I have everything on this system working now!!  Sent a successful fax already!

Thanks for the help!
-Matt

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=Matthewb57]Turns out the modem was a serial modem and was controlled through ttyS2.  I installed Minicom and switched ttyS? until I found it to be ttyS2.  Thanks for the info about the modem wiki.  I believe I have everything on this system working now!!  Sent a successful fax already!
[/QUOTE]
Now I'm incredibly jealous... :KS

---

