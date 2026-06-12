---
title: "Trouble trying to use Live CD"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by tvanryn on 2008-01-05
Hello, I am trying to boot to Ubuntu using the Live CD and am having the following issue:

(Keep in mind I have tried this with a CD image I downloaded, and with the Ubuntu CD from ShipIt, and I get the same result)

When I boot I get the install screen.  If I choose either "Start or install Ubuntu" or "Start Ubuntu in safe graphics mode" the kernel loads, and I end up with a black screen with a blinking cursor in the upper left corner.

After lurking around these forums I found the "press F6 and delete "quiet" and "splash" solution.  This gets me to a screen of text (after repeating the steps in the previous paragraph) but then it hangs.  The last line of text is "[ 190.471632] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found."

My hardware is:

ASUS P4P800
Intel P4 3.0
2 GB RAM
ATI Radeon 9600

Please help.

---

### Post by exneo002 on 2008-01-05
first which edition is it I've tried ubuntu 7.10 and had to burn it twice to get it to work 
second if its 6.06 its hardware support sucks 

If you are having these problems and you have cable or dsl I recommend trying ubuntu ultimate edtion 1.6 and linux mint
If you havent tried kde go for pclinuxos opensuse mandriva and maybe fedora [gnome or kde]
go with gnome fedora or somthing else remeber ubuntu isn't the only linux distro

---

### Post by tvanryn on 2008-01-05
It's 7.10.  I've got a CD of Kubuntu on the way as well, so I'll try again with that, but I'd really like to see Ubuntu up and running.

---

### Post by Yoke &amp; Chung on 2008-01-05
My suspicion is on your graphics card. If you have another spare old graphics card, or onboard graphics, switch around and see you can boot the LiveCD.

Some newer cards have a hard time working with LiveCDs. I have the same problem as you with my nVidia 8600GTS card.  I tried all my LiveCDs-- Xubuntu, Kubuntu, Ubuntu, and even PCLinuxOS, non of them works with the card.

---

### Post by tvanryn on 2008-01-05
So, I won't be able to install at all, or just not use the Live CD?

---

### Post by Yoke &amp; Chung on 2008-01-06
> **tvanryn said:**
> So, I won't be able to install at all, or just not use the Live CD?

You are still able to install. I can think of 2 options here.

1.) Use alternate CD installation. I have not done this personally but read that this solves problems for many nvidia 8600 GTS users.

2.) Alternatively you can install LiveCD using an older graphics card, then disable the restricted driver. Log into console, and install the correct driver for your new graphics card while you are still on the old graphics card, reboot, and you are done. I have no experience with ATI cards, so I couldn't give more info on how to install your ATI driver. This is the method I used to get my card working in ubuntu. In fact, I did the same way for my Windows XP boot as well cos Windows also give the same problem of black screen after boot up. (Initially I thought it was due to hardware problem)

First, confirm whether it is the graphics card issue, though the symptoms do look like what I have experienced, do double check.

Secondly, search around on how to install the correct driver for your ATI card, especially if you want to go route 2. Write down/ print the procedures and make sure you follow them correctly.

Good luck.

---

### Post by Alacard on 2008-01-06
I recently installed it on my laptop it would give me that black screen with the blinking cursor too, after a while it finally gave me an error kernal panic not syncing. Did some reading online and did a memory test...turned out it was a bad ram chip, took it out and never had the problem since. Something to think about good luck

---

