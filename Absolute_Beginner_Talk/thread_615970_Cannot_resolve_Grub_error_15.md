---
title: "Cannot resolve Grub error 15"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Red David on 2007-11-17
I have been all over the various threads and links concerning GRUB and the type 15 errors and made essentially NO progress. On my machine the drive (set to slave) with XP is physically disconnected. I have tried installing 7.10 and 7.04 on two different drives (both set to master, both IDE and removing one when trying the other) to no avail. Installing from the live CDs seems to take place but I have not been able to reboot. I chose the guided installation use entire disk option, takes awhile, indicates that it is creating the "Partition # 1 of IDE 1 Master (hda) as ext 3 and #5 etc as swap" and so forth. Try rebooting and I get the error 15. 

I don't claim to be all that terminal savvy but I have tried all the main suggestions, including starting in safe graphical mode etc. NO LUCK! I'm continually told, in effect, that the device does not exist. Which is complete BS. Right now, to have other than a piece of junk on my hands, I would have to disconnect the linux drive, re-set the XP drive to master and just give up. If I could afford to buy a virgin IDE drive I suppose I could try installing on that. But I can't.

I don't mean to step on toes, but Ubuntu's claim to be the linux for everyone is way overstated. Frankly, the linux for everyone is OS X. I acknowledge the power of the terminal/cli and how much fun, even, that it might be. But the everyday user should NEVER have to use it except for either the most esoteric of elective purposes or the most extraordinary and dire circumstances. And a basic install/upgrade does not qualify. Or shouldn't.

At this point, I'll probably waste some time on occasion trying to get a working installation again but I'm back to my powerbook. I figure I could dink around in the OS X terminal, hose my system and still start from scratch with the CD and be back in business.

Anyone in the Seattle area reading this is welcome to come look over my shoulder and help me figure this out.

d

---

### Post by markk1994 on 2007-11-17
Hey I had the same problem like 1 month ago here is how I resolved it.
I downloaded and installed Super Grub Boot Disk which is an iso about 3 mb in size.
When you boot it you have to look for the menu to restore your MBR and it uninstalls grub and then you start it up agian and install grub and it should work perfectly.
Give it a try and msg me back if it doesnt work

---

### Post by Pumalite on 2007-11-17
It could also be a bad burn. Do md5sum on your iso, burn at 4x in good CD-R media. Try your CD's in a different computer. I would also try the Alternate CD if the Live CD is a no go.

---

### Post by Red David on 2007-11-17
Thanks, guys. I've pretty much ruled out defective cd or cd drive causes. The 7.04 Ubuntu is an official Canonical cd as is the 7.10 Kubuntu. I also verified my burns on the discs of both versions I did myself. My original functioning 7.04 Kubuntu install was from my own burn.

As to Super Grub, how do I install it? I downloaded and burned it on my powerbook (correctly, I think) but the pc wouldn't boot from it. Since I can only get the machine to run on the live cd, I don't see how I can install or run Super Grub. What am I missing here?

d

---

### Post by Pumalite on 2007-11-17
I don't think Super Grub was meant to boot in a Powerbook. I could be wrong. Where are you installing?. Powerbook or PC?. If Powerbook; Intel?. Give more details of your system and what you are trying to accomplish. Specs would help. Also, I would download my own iso and do an md5sum on it before burning. That they sent you the disk is no warranty.

---

### Post by Red David on 2007-11-17
Sorry for the confusion. I downloaded Super Grub on my powerbook (as my pc is essentially unusable) and burned the image. I then attempted to boot my linux machine with it, to no avail. Macs burn ISOs perfectly well. I also did the verify disk on everything, as far as I know.

d

---

### Post by Pumalite on 2007-11-17
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Red David on 2007-11-17
Ok, re Super Grub: I re-burned the ISO and it "works." I use quotes because it boots (should be in " " also) to a screen that doesn't give any recognizable menu, just the instructions that TAB lists possible command completions, etc. Typing tab at the grub> prompt is not at all helpful as the list of commands is rather beyond my comprehension.

Step by step from this point, anyone.

d

---

