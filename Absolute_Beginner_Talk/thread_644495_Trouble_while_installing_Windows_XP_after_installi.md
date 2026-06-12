---
title: "Trouble while installing Windows XP after installing Kubuntu.. HELP PLEASE!!"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by lxgshaka on 2007-12-18
I need some help.. 

I have a laptop (HP Compaq nx7400) which I was asked to format and reinstall WinXP.. but when I started the windows XP installation it gave some errors while reading the disc's files.

Then I installed Kubuntu just to try, and it installed perfectly.. 0% problems..

Now I try installing XP again and it says it can't find any Hard Drives.. in the PC

Then, I tried formatting the disc to NTFS using GParted LiveUSB and.. nothing, same problem.

I ran Norton Disk Doctor from hiren's bootcd, an extensive disk check and no problems at all with the HDD.

I don't know what else to do.. I tried installing XP under VMWare but that's not what this guy wants.. he only knows windows xp and kind of needs it for his work.

Well, I hope you can help me because It's been over 3 days of staying up past 4am an no luck yet.

Thanks a lot!

---

### Post by heatpumpcontrol on 2007-12-18
have you checked the bios? make sure the hd shows up. Even if it does, just do a reset of the bios or you may want to have the bios autodetect the hds again. Sounds like a glitch.

---

### Post by lxgshaka on 2007-12-18
i'll try that.. thanks, but the thing is.. that all software I use, Norton Disk Doctor, GParted, etc.. all detect the hard drive.. and Kubuntu does fine too.. 

I've heard is the format of the disk.. but I don't know... well.. I'll try that and edit =) or write with results ^^

---

### Post by cp1969 on 2007-12-18
If you don't have any data that you will lose, just format the disk, partition it however you see fit (I did three--1 for XP, 1 for ubuntu, and 1 for spare or data), install XP, then install Kubuntu.  

That's the way I did it with ubuntu and then it automatically installs GRUB which is a bootloader program.  Then when you boot, it gives you the choice of which OS you want to use.

But I think XP has to be installed first.

edit:  On second thought, formatting is probably not what you want to do.  I started with a clean disk and let XP format its partition but nothing else.  Ubuntu and its sister OS's format their partitions in a manner, at least on my machine, such that XP can't even recognize them.  So formatting under Windows is probably not the answer.

---

### Post by lxgshaka on 2007-12-19
> **cp1969 said:**
> If you don't have any data that you will lose, just format the disk, partition it however you see fit (I did three--1 for XP, 1 for ubuntu, and 1 for spare or data), install XP, then install Kubuntu.  

That's the way I did it with ubuntu and then it automatically installs GRUB which is a bootloader program.  Then when you boot, it gives you the choice of which OS you want to use.

But I think XP has to be installed first.

edit:  On second thought, formatting is probably not what you want to do.  I started with a clean disk and let XP format its partition but nothing else.  Ubuntu and its sister OS's format their partitions in a manner, at least on my machine, such that XP can't even recognize them.  So formatting under Windows is probably not the answer.

that's what i'm trying to do.. but after I installed ubuntu.. the windows installer cant find the hard drive :S so it cant format >_<

---

### Post by RockHaxor on 2007-12-19
On your laptop ,disable the native SATA under BIOS and install the SATA drivers after Windows installation. The installation disk may not have the SATA drivers required and therefore cannot find the drive. 

Good Luck

---

