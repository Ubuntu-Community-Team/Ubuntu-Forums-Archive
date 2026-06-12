---
title: "Should I just go back to Dapper?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Hildsvfar on 2007-08-12
I'm really getting sick of freezing, and I keep having this problem when I reboot.  Whenever I reboot, my bios loads info on my hard drives, then just freezes there.  When I've run live discs and rebooted I haven't had any problems...  Then again, I just built this PC last week and I've only run Feisty on it so far.  I like pretty much everything except for the fact that it freezes so much...  And that I can't exactly well... reboot.

I just don't want to downgrade and not be able to use a lot of the programs I'm currently using...  I dunno what to do.  I used Dapper for a long time with hardly this many problems on my old computer, but I'm really sick of having to hold down the power button on this computer when it freezes.

that's another thing, sometimes when it freezes and I press the off button, the logout/poweroff menu will pop up.... it's not like I can use it if my keyboard and mouse are frozen, so it's almost like the computer is teasing me lol.

---

### Post by Spr0k3t on 2007-08-12
Sounds like there is definitley a problem, but not at the OS level... somewhere at the harddrive level.  Check your bios for drive handling on the system... see if you can remove caching or change the level of buffering to something like compatibility mode.

---

### Post by Hildsvfar on 2007-08-13
I feel kinda dumb saying this, but I can't figure out how to do what you're saying from my bios...  I have an EVGA Nforce 650i Ultra motherboard and my hard drives are hooked up through SATA, and my dvd drive through IDE.  And I have an intel core duo if that helps...

---

### Post by hanzomon4 on 2007-08-13
Check your swap space free -m

---

### Post by PriceChild on 2007-08-13
**You rebuilt it**... then feisty on it doesn't work properly but you blame Ubuntu?

---

### Post by diatribe on 2007-08-13
> **PriceChild said:**
> **You rebuilt it**... then feisty on it doesn't work properly but you blame Ubuntu?

haha

---

### Post by Hildsvfar on 2007-08-14
> **PriceChild said:**
> **You rebuilt it**... then feisty on it doesn't work properly but you blame Ubuntu?

I never said I **RE**built anything, these are all new parts.  Why respond if you're not going to even try to be helpful?

---

### Post by Jimmyfj on 2007-08-14
You'd get a long way if you did probe the computers hardware in a step by step approach. Process of elimination. 

First thing you do is to enter your BIOS at startup. This can be done by hitting either the Del-button or F2 >> F12, some computers use the Del button others one of Function buttons. Then you start by loading the BIOS Default Setup settings and try to reboot after a save. 

If the computer still wont reboot from your OS then more drastic measures are appropriate starting with disconnecting one hardware device at a time until you find the faulty part. This obviously IS a hardware problem **NOT** a problem with the OS. Ubuntu isn't to blame for this, your hardware is.

For your information, I run two computers with SATA disks mounted on both. NONE of those have the problem you descripe. My WS is running Gutsy 7.10 and I have NO issues with my 200 GB SATA hard drive.

---

### Post by Gone fishing on 2007-08-14
It's supposed to show the logout menu when you press the power button, oddly, I did have a similar problem to yours on my other PC - turned out to be a poor SATA cable not saying yours is that but it sounds like hardware.

---

### Post by Hildsvfar on 2007-08-14
I'm gonna try and figure it out thursday or friday, when I finally have a day off from work.  I'll post what the problem is when I figure it out.  Thanks to anyone who took the time to help!

---

### Post by Hildsvfar on 2007-08-16
Okay so the problem ended up being my wireless card and ndiswrapper.  I just found it kind of weird that it didn't have any problems until I installed ndiswrapper and got it working.  I also found it kinda weird that I'm having absolutely no problems now with this wireless card because it's the same thing, only an older revision I guess.  They're both Trendnet TEW-423PI wireless cards, but somehow the older one works a lot better with my computer.

---

