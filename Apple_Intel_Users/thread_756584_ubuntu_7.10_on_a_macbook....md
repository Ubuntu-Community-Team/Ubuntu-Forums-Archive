---
title: "ubuntu 7.10 on a macbook..."
date: 2008-04-16
forum: Apple Intel Users
---

### Post by turcott on 2008-04-16
hey i just installed ubuntu 7.10 on a macbook, so far so good.  Only problem is the boot up time, when you turn on the notebook the screen stays white for awhile before ubuntu loads up.  Is there a way I can eliminate this lag in between, it alone must be 30 sec or possibly more before ubuntu loads.  i'm running an intel core 2 duo, 2.2ghz, 1.5gb ram.

---

### Post by plasmatonic on 2008-04-16
That delay is the EFI Bootloader determining what device to boot, and then loading the BIOS Compatability layer. It is unavoidable until Ubuntu can (natively / fully) support EFI 1.1.

---

### Post by thenes on 2008-04-16
Are you dual booting or only running Ubuntu on your mac book? If you are dual booting, you can check out [rEFIt]("http://refit.sourceforge.net/"). I do not know if it will help the time your machine uses to find the partition you want to boot, though, but it is very practical if you are dual booting.

---

### Post by ronocdh on 2008-04-16
> **thenes said:**
> Are you dual booting or only running Ubuntu on your mac book? If you are dual booting, you can check out [rEFIt]("http://refit.sourceforge.net/"). I do not know if it will help the time your machine uses to find the partition you want to boot, though, but it is very practical if you are dual booting.
This is correct. By installing OSX on a small partition and using rEFIt, you will substantially reduce the amount of time your computer takes to boot up. You can set Ubuntu as the default OS in rEFIt, as well as reduce the timeout to 1 or 2 seconds. Then GRUB will chainload in and if that timeout is also an appropriately small value, then you'll be booting Ubuntu in no time.

Remember that you need an OSX installation at least for firmware updates. Pare it down, but keep it around, I say.

---

### Post by turcott on 2008-04-16
No the HD in the Mac was formatted when i got it, so i installed ubuntu 7.10, works great so far (after a few tweaks), but the white screen delay before ubuntu loads is like 30 secs or more.  So it's the EFI Bootloader determining what device to boot, why does it take sooooo long.  I have a pc laptop that's only a pentium 2, with only 128mb of ram, and a small 8gb hd, with win xp on it and it loads faster than the Macbook, lol...just wondering why it takes so long and if i can install a software or redue the delay somehow??!

---

### Post by cyberdork33 on 2008-04-16
> **turcott said:**
> So it's the EFI Bootloader determining what device to boot, why does it take sooooo long.Because it does as has been explained. Since you completely reformatted your Hard drive, it was probably converted to the legacy MBR format partition table and not the GPT format that EFI expects. It searches long and hard for a GPT capable device before reverting to booting the normal MBR table. There is currently no way to change this delay.

---

### Post by turcott on 2008-04-16
k, thanks everyone for the feedback, i guess this issue is normal and unavoidable at this time.  Just wondering if I converted the HD to the legacy MBR format partition table and not the GPT format that EFI expects, could i go back and install ubuntu again and with a GPT format so that EFI will recognize it quicker?

---

### Post by cyberdork33 on 2008-04-16
> **turcott said:**
> k, thanks everyone for the feedback, i guess this issue is normal and unavoidable at this time.  Just wondering if I converted the HD to the legacy MBR format partition table and not the GPT format that EFI expects, could i go back and install ubuntu again and with a GPT format so that EFI will recognize it quicker?
yes you could do that. gparted is capable of making GPT disks, but the option is not apparent.

---

### Post by PartisanEntity on 2008-04-17
> **turcott said:**
> hey i just installed ubuntu 7.10 on a macbook, so far so good.  Only problem is the boot up time, when you turn on the notebook the screen stays white for awhile before ubuntu loads up.  Is there a way I can eliminate this lag in between, it alone must be 30 sec or possibly more before ubuntu loads.  i'm running an intel core 2 duo, 2.2ghz, 1.5gb ram.

How easy/hard was it to install Gutsy on the Macbook? What did you have to tweak?

I would like to install Gutsy on my Macbook, next to OSX, so I am trying to gather as much info as possible before I go ahead.

Thanks very much.

---

### Post by cyberdork33 on 2008-04-17
> **PartisanEntity said:**
> How easy/hard was it to install Gutsy on the Macbook? What did you have to tweak?

I would like to install Gutsy on my Macbook, next to OSX, so I am trying to gather as much info as possible before I go ahead.

Thanks very much.how old is your macbook? There are various hardware changes that have been made over time.

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by PartisanEntity on 2008-04-17
Its 1 week old.

---

### Post by turcott on 2008-04-17
It was extremely easy to install Ubuntu on the Macbook, mine is older than yours and i had no major issues.  The only hardware changes you need to make is, setting up the touchpad so you can use it to click items, a keypad patch, and a device driver for the wifi card, (you should be able to find the fixes here).   Other than that Ubuntu works well so far.  Mac OS is efficient cause it's much like Linux, actually very much the same.  Depending on what distro your using, but in comparison both OS X and Ubuntu are user friendly, have a nice, and clean GUI, stable and very few bugs/glitches.  Though for me since Ubuntu is open source that is mainly my reason for that install.

All in all in my opinion a Mac is really no different than a PC, it's mainly the hardware inside and what code/instructions they use to tell the cpu what to do, as well the architecture and design of the chipset.  It's like sony ps3 vs xbox 360, games won't run as well or at optimal performance if the game was designed for xbox 360 then ported to the ps3.  If the game is designed based on the specs for that distict system, you then are able to utilize and take advantage of it's hardware capabilities.  The Mac runs better cause to me it does what it needs to do at that given time, not like a PC running a bunch of apps/programs in the background utilizing resources and sacraficing performance.

---

