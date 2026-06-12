---
title: "New Install - First Timer"
date: 2006-10-24
forum: Apple PPC Users
---

### Post by CadTeach on 2006-10-24
Hi All,

Typing this in firefox on my newly installed Xubuntu on a imac 233 mhz G3 I picked up at a garage sale this weekend. For $50, it looks like I got what I wanted, which was a chance to try out Linux for the first time and start learning something new. 

Install went very smoothly, only had to edit the refresh rates for the screen, as found on these forums. 

Hardest thing was trying to get the iMac to boot from cd. I'm not a mac user, so I had to dig up some info, holding down c wasn't helping. 

Must say I'm so far impressed by what you get for so little effort.  I'm anxious to try some of the other apps.  Any suggestions?  

Appreciate all the help available, this is a great resource. 

:)

---

### Post by meng on 2006-10-24
Welcome, and always feel free to ask for help. (Myself, I try not to comment on anything that looks Mac-architecture-specific, since I don't have the experience.)

---

### Post by Gimlet on 2006-10-24
Hey I also have G3 with Mac OS 8.1 on it but want to install ubuntu. I also cannot get it to boot from cd can you explain how that works.

---

### Post by CadTeach on 2006-10-24
Sure,

Do a search for open firmware. It's like a terminal window in Mac, which can be opened during startup by holding apple-option-o-f keys. You must have the live cd in the tray.  Then there is a boot command from there, at the openfirmware prompt, type: 

boot cd:,\\:tbxi 

It should boot from the cd.  I ended up having to burn 2 live cd's, the first didn't work, may have been a bad burn. You may have to try it a couple times.

From there, you may also get the dreaded black screen, which I did, also well documented here.  It basically requires you to edit a file and chenge refresh rates for the monitor. 

Hope it helps.  It's all here, just keep searching.

---

