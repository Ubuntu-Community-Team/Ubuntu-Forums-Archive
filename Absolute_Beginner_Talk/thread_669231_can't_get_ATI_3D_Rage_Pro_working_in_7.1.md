---
title: "can't get ATI 3D Rage Pro working in 7.1"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by akai11nj on 2008-01-16
I have a workstation which (sometimes) dual-boots XP Pro and 7.1 Gutsy. Here's the problem.
The computer is an HP with an Intel 82810E integrated graphics chipset and a ATI 3D Rage Pro PCI card. I couldn't install Gutsy, version 7.1 using the Rage, so I disabled it in Windows, enabled onboard video in BIOS and successfully installed Gutsy on a second hard drive. No problems : it installed smoothly and works excellently. But I would like to use the ATI card, which works just as excellently in Windows. Obviously if I reverse the steps I've taken to install Ubuntu, the system crashes. X won't start. 
I'm fully capable of reverting back to onboard video (I've been using the ATI and booting exclusively into Windows until I find a solution to this problem).
Any input or assistance that anyone can offer would be greatly appreciated.
Thank you.
Rich Dennis

---

### Post by overdrank on 2008-01-16
> **akai11nj said:**
> I have a workstation which (sometimes) dual-boots XP Pro and 7.1 Gutsy. Here's the problem.
The computer is an HP with an Intel 82810E integrated graphics chipset and a ATI 3D Rage Pro PCI card. I couldn't install Gutsy, version 7.1 using the Rage, so I disabled it in Windows, enabled onboard video in BIOS and successfully installed Gutsy on a second hard drive. No problems : it installed smoothly and works excellently. But I would like to use the ATI card, which works just as excellently in Windows. Obviously if I reverse the steps I've taken to install Ubuntu, the system crashes. X won't start. 
I'm fully capable of reverting back to onboard video (I've been using the ATI and booting exclusively into Windows until I find a solution to this problem).
Any input or assistance that anyone can offer would be greatly appreciated.
Thank you.
Rich Dennis

HI  and welcome, since you have Ubuntu installed then you can try and reconfigure your xorg from the command prompt. If you boot into recovery mode ( which is usually the second choice in the grub) then use this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` And use the command ```
reboot 
``` or startx and hopefully this will get you to the GUI.

---

### Post by akai11nj on 2008-01-17
When I've tried booting into recovery mode, all I get is a black screen - not even a CLI. Just a blank black screen.

---

### Post by akai11nj on 2008-01-21
Okay, so I've managed to get into the Recovery Console and run lspci to get the bus settings (01:08:0) for my ATI 3D Rage Pro PCI. Then run sudo dpkg-reconfigure xserver-xorg. Using the bus settings from lspci, I've been able to complete the hardware redetection and run startx and get to a graphical Gnome session. Display looks perfect. 
However, when I exit back to the CLI and reboot, I get an error msg. after booting to the generic kernel that this video mode can't be displayed.
I've established that it can, doing the dpkg-reconfigure. I'm guessing that the values aren't being saved correctly to the xorg.conf file? Am I right? It's really irritating to being this close to resolving a problem and still be at a loss. Anyone have any ideas what I'm doing wrong? I'm running the sudo dpkg-reconfigure as root, so my permissions should be correct. Shouldn't they? I'm stumped.
Thank you to anyone willing to help a Linux amateur.
R.Dennis

---

### Post by akai11nj on 2008-01-21
Managed to boot back into XP and using an ext2 reader that I've installed and Wordpad, I took a look at the Xorg.conf file. Everything looked the way it should, so I tried rebooting again into Gutsy, and after a brief "This video mode cannot be displayed" blank black screen, my Gnome login window popped up. Logged in, checked everything out, looked good. Ran some updates. Can't wait for Hardy Heron to come out, even though this particular machine will probably be completely unable to run it (but I can hope).
Long Live Linux!! Awesome!!
R.Dennis

---

