---
title: "blank purple screen after GRUB menu - Asus Q500A"
date: 2013-01-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by eloist on 2013-01-24
Brand new laptop, came with Windows 8. Asus Q500A - (Best Buy model).

Trying to set up dual boot for LAMP stack web dev setup. Currently I'm in a web dev school. Need to keep Win8 for Adobe CS6.

Installed 12.10 on a new partition via USB thumb drive.
Could not boot into Ubuntu.

Ran boot repair via live disc (USB stick).

Now I have GRUB options on boot of the machine, but selecting Ubuntu results in blank purple screen. Does nothing at all, forces me to hard reset. I've been searching for a fix and have gone down multiple rabbit holes with no positive results.

This is the pastebin link I got after running boot repair:

[http://paste.ubuntu.com/1567906/](http://paste.ubuntu.com/1567906/)

Once again, I can see the GRUB menu when i start the laptop, but selecting Ubuntu results in a blank purple screen and goes nowhere. I am able to boot into Windows 8 just fine, thankfully.

I'm extremely new to Linux. Need your help.
I was able to set up a 100% perfectly working 12.10/Win 8 dual boot on my non UEFI (X58 BIOS) desktop, but I am stuck on the laptop.

:confused:

Thanks in advance.

---

### Post by iamthenewguy on 2013-02-20
i have seen people with similar problems on win 8 laptops and from what i can tell, you may need to switch from 32 bit ubuntu to 64 bit. hope this helps.

---

### Post by atrh on 2013-02-23
I dual boot win 8 pro(x64) and ubuntu 12.04(x64) on Asus A45v and it's working well.
I kinda have the same problem with you at first but after boot-repaired,the problem solved.
I ain't sure but you need to think about the graphic card and its driver.

---

