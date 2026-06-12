---
title: "Joli OS Install Problem - White Screen"
date: 2013-03-04
forum: Any Other OS
---

### Post by eldavar on 2013-03-04
I'm new to this forum, and relatively new to Linux in general, so Iapologize in advance if I'm making noob mistakes... ;-) 

I've been trying to install Joli OS on an old laptop. I played with the online desktop version and it looks like a good fit for my kids (5 & 8) because it's pretty simplistic. But no matter how I try to do the install, I keep ending up at a completely blank white screen. I [asked for help]("https://getsatisfaction.com/jolicloud/topics/install_failure_white_screen") at the Joli community on GetSatisfaction, but there was very little response and none of it was helpful. I'm hoping someone here can help me. 

The laptop is a Toshiba Satellite Pro 6100. It boots from the CD without issue and begins the install, but after a few minutes the screen turns white and nothing else happens. I've let it sit for hours, but nothing changes. I can hear the CD drive working, and my guess is the installer is waiting for input from me (location, language, etc.). But it won't display on the screen. 

If I press the Esc key during the install, the generic splash screen switches to a text dialogue and I can follow the progress. Initially, errors appeared about firmware files not found (b43/ucode5.fw). I figured out that related to the PCMCIA wifi card, so I pulled it out. Next time those errors didn't appear but I got the same white screen, so obviously the two are unrelated. I figure I can handle getting wifi running later, once I get the actual OS running. 

When the ISO install didn't work, I decided to try the Windows installer. Not my preferred method but since this is just for my kids to play on I said ok. I installed a fresh copy of WinXP after formatting the drive, and that went without problems. I downloaded the Joli Windows installer, it started up fine and looked the same as the ISO when it began. But it also brought me a blank white screen. So if I'm thinking correctly, this means the issue is with my hardware. The laptop has not been modified, it's not damaged, it's just old. It runs WinXP as you'd expect, and as a test I installed another Linux distro and that had no problems. 

From the Joli install splash screen, if I press the Esc key I get a terminal with "boot:" where I can type something. If I choose Help from the splash screen, I get some generic info about using boot parameters if the install is having trouble. I've tried them all, both individually and together in combinations, but nothing works. Still the same white screen. Here's some examples of what I've tried (plus many other combinations too):
```
live-install noapic nolapic
live-install vga=788 fb=false
live-install no387 apic=off
live-install hw-detect/start_pcmcia=false pci=noacpi
```
You get the idea. Since the help screen says Joli OS is based on Ubuntu 10.04, I read the troubleshooting section of the guide on this website. There is [one mention]("https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html#i386-boot-problems") of a white screen and it says "[SIZE=2][FONT=arial][COLOR=#000000]If your screen begins to show a weird picture while the kernel boots, eg. pure white, pure black or colored pixel garbage, your system may contain a problematic video card which does not switch to the framebuffer mode properly.[/COLOR][/FONT][/SIZE]" It then says to use fb=false and/or vga=788, neither of which worked. 

And that's where I am now. I've tried everything I can think of and don't understand why I keep getting the white screen. Any help or suggestions would be greatly appreciated. Sorry about the length of this post too, but I wanted to explain what I already did so it can help the experts here.

---

