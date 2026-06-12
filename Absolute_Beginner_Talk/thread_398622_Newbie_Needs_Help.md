---
title: "Newbie Needs Help"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by 1205919 on 2007-04-01
Hi this is my first post

Im brand new to Linux and therefore Ubuntu.
Im trying to install UBUNTU 6.10 on my pc but the installer doesnt pick up my hdd.
I want to overwrite the current windows xp installation which is resident on said disk. The disk is a seagate 250gb.
The windows installation still works fine. Its just ubuntu that wouldnt pick up the hdd.
I have tried two different iso's but get the same problem. ive tried the ubuntu-6.10-desktop-i386 and the ubuntu-6.10-alternate-i386
Please help I really want to get Ubuntu up and running...

---

### Post by overdrank on 2007-04-01
> **1205919 said:**
> Hi this is my first post

Im brand new to Linux and therefore Ubuntu.
Im trying to install UBUNTU 6.10 on my pc but the installer doesnt pick up my hdd.
I want to overwrite the current windows xp installation which is resident on said disk. The disk is a seagate 250gb.
The windows installation still works fine. Its just ubuntu that wouldnt pick up the hdd.
I have tried two different iso's but get the same problem. ive tried the ubuntu-6.10-desktop-i386 and the ubuntu-6.10-alternate-i386
Please help I really want to get Ubuntu up and running...

Hi and welcome, If you could give us some specs on your system then we maybe able to help. Are you using sata raid? I have seen some problems with this.

---

### Post by 1205919 on 2007-04-01
Hi sorry for omitting the specs:

Intel Core 2 1.86ghz
2Gb Ram

i dont think its a raid system as the single hdd is atached with a normal ide cable which runs as a master disk

What other type of info might you need.
Please pardon my ignorance as im not very tech inclined

Thx

---

### Post by Lucifiel on 2007-04-01
Are you still able to load into your WinXP o/s?

If so, download this utility from the internet: aida32. It'll read all your system information. Or try this software : mvpcinfo . Both do the same, really. If I'm not wrong, both softwares have the ability to save your hardware information into a log. So, save your system information into a log and paste it into your post.

---

### Post by 1205919 on 2007-04-01
Hi Me again

Thx to all for the help.

Ive produced 2 reports, one just a system report the othr a full hardware report

I hope this will help you guys to help me :) 

Ive attached the reports as zip files as plain txt, its 2 big

---

### Post by confused57 on 2007-04-01
Might be a setting in your bios for your hard drive IDE controller that needs changing.  I just helped someone in another thread, he had  changed his bios setting from "Normal" to "Compatibility" & the Kubuntu live cd wouldn't recognize his hard drive...may be something similar in your bios.
Just change one thing at a time & try it...I'd write down exactly what was changed, so you can change it back if there's a problem.

Added:  If you're using a PCI IDE adaptor, you may have problems getting Linux to recognize your hd.

---

### Post by 1205919 on 2007-04-01
Thx for that.  How would I know if im using a PCI IDE adapter. The cable is going from the hdd straight on the motherboard:confused: 

> **confused57 said:**
> Might be a setting in your bios for your hard drive IDE controller that needs changing.  I just helped someone in another thread, he had  changed his bios setting from "Normal" to "Compatibility" & the Kubuntu live cd wouldn't recognize his hard drive...may be something similar in your bios.
Just change one thing at a time & try it...I'd write down exactly what was changed, so you can change it back if there's a problem.

Added:  If you're using a PCI IDE adaptor, you may have problems getting Linux to recognize your hd.

---

### Post by oilchangeguy on 2007-04-01
as long as the cable is going from the mobo to the drive, it's not pci. most computers do not have pci controller cards installed.

---

### Post by 1205919 on 2007-04-01
I cant find any setting in bios that relates to something like normal or compatability. All I see is a setting legacy or native. Changing that doesnt seem to make a diff:confused: 

> **confused57 said:**
> Might be a setting in your bios for your hard drive IDE controller that needs changing.  I just helped someone in another thread, he had  changed his bios setting from "Normal" to "Compatibility" & the Kubuntu live cd wouldn't recognize his hard drive...may be something similar in your bios.
Just change one thing at a time & try it...I'd write down exactly what was changed, so you can change it back if there's a problem.

Added:  If you're using a PCI IDE adaptor, you may have problems getting Linux to recognize your hd.

---

