---
title: "Ubuntu no longer boots, no changes made"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Okie Dokey on 2007-08-11
Hello,
I stumped. I have ubuntu installed on a system with a single hard drive.  On that drive is an installation of XP, but it wasn't set up as a dual boot.  I don't use the xp instalation for anything.

When I installed Ubuntu, I had some problems, but I thought I overcame them.  The problem was that the both cd drives had jumpers in as Slaves.  I figured this out later.  At the time of installation, I used a CD drive from another computer (with jumper as master).

Anyhow, I noticed a strange thing. Even after Ubuntu was installed and I had been learning it, it never booted without the cd in.  Does Ubuntu always need the CD?  Seems silly.  It starts then searches for ide, then prompts for "boot from cd" counts down then the cd spins up, I guess it uses the GRUB on the CD.    It is very slow.  Sometimes it loads and I can use Ubuntu (Feisty Fawn) and other times it doesn't.  When it doesn't I hit the reset on the system, or sometimes turn the power off and try again, it still boots really slowly but it seems to eventually load. 

I really think this has something to do with the bios settings, it takes a long long time to detect ide drives, like 30 seconds. I have 2 computers that I'm working on as I'm typing this, one ubuntu the other windows. After 5 tries at booting up ubuntu I changed the bios to FailSafe Defaults, then Ubuntu booted up.  

Nonetheless it seems that I need the CD in.  Is this how this is supposed to work?

---

### Post by bodhi.zazen on 2007-08-11
sounds like you need to install grub to the master boot record.

See this link : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

* Don't let the title throw you ;)

---

