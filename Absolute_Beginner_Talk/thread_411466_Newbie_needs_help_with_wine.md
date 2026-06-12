---
title: "Newbie needs help with wine"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by kaxx on 2007-04-16
Hey guys, this is my first post on here. I gotta say I am really starting to like this Ubuntu OS. It's creating some new challenges for me and I hope to be M$ free before long. 

Anyway to the point, I'm trying to figure out if I have wine installed right. When I type wine --version in terminal I get wine 0.9.35. But when I try to Install Diablo 2 with the .exe program on the disk, it hangs for a short while and then nothing happens. I'm sure this is a simple fix, but I'm rather clueless with this OS as of now (only had it installed for 3 days now). Can anyone point me in the right direction?

---

### Post by Fitzy_oz on 2007-04-16
> **kaxx said:**
> Hey guys, this is my first post on here. I gotta say I am really starting to like this Ubuntu OS. It's creating some new challenges for me and I hope to be M$ free before long. 

Anyway to the point, I'm trying to figure out if I have wine installed right. When I type wine --version in terminal I get wine 0.9.35. But when I try to Install Diablo 2 with the .exe program on the disk, it hangs for a short while and then nothing happens. I'm sure this is a simple fix, but I'm rather clueless with this OS as of now (only had it installed for 3 days now). Can anyone point me in the right direction?

Good to see you're enjoying Ubuntu, Diablo 2 is very well supported by wine so you won't have too much trouble if any.  Here's the deal:

Open a terminal and type winecfg as you will need to generate the user specific folders and registry settings in order for wine function correctly.
Once this is done you should be able to navigate to your cd-rom drive in ubuntu, right click on the setup.exe file and select the *'open with wine windows emulator'* or something to that effect.  Failing that, you can do it manually by opening a terminal and typing 'wine /media/cdrom/setup.exe'

Good luck and shout out if you need anymore help.  ;)

---

### Post by kaxx on 2007-04-16
Ahhh, yes. Thanks Fitzy. I knew Diablo was supported hence the reason I'm starting with that very old (but still cool) game. OK.....on with the install!!

Thanx again

---

### Post by kaxx on 2007-04-18
Hey guys, back again with another question. I've tried following guides that are here on this forum (and did a google search) but for some reason the Diablo install freezes. I get to the point that it asks for a desktop icon, (I've checked both yes and no on different occasions) and the install progress bar just freezes with absolutely no progress. I can't exit out of this or even move the install progress box. I end up rebooting the PC to get it back to normal. I'm guessing my Wine isn't configured properly, perhaps??? Under default settings I've tried both windows 98 and XP and the default windows 2000. Sorry this is so long, I just want to answer any questions you may have

Please help this Ubuntu newbie......

---

