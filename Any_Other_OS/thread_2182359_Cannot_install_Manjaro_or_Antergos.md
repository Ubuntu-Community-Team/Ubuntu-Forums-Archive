---
title: "Cannot install Manjaro or Antergos"
date: 2013-10-21
forum: Any Other OS
---

### Post by su:bhatta on 2013-10-21
Hi all,

I have been trying to install Manjaro Gnome & Antergos in 2 HDD partitions that I was experimenting with Ubuntu Devel release. But cannot get a live session in either.


In both cases with the use of 'nomodeset' I am getting the final CLI screen, after all [ok] boot messages,  which says  'Started GDM' & 'Target Reached Graphical Interface', but i am not getting a GUI. 
The operation freezes in that CLI screen. 

I have to use 'nomodeset' for installing Ubuntu(all flavors) and 'no splash nomodeset' when I had installed Fedora19.

Attaching my lspci, in case that helps.

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
05:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```

Any help is appreciated. I have a working Debian Wheezy which did not require any kernel args, btw.
Currently using Ubuntu Gnome, which was installed with 'nomodeset' & added all metas from Ubuntu Studio.

---

### Post by Allavona on 2013-10-21
A quick glance at the Antergos Forums says that your not the only one!. When I played around with Antergos I switched the resolution at the boot screen. F3, I think, to 1024X768. It booted right into Gnome. Never installed it, but it hangs on boot too after install.

Manjaro Gnome is a community respin so I don't know how much help you'll get there. I was able to boot fine into the openbox default manjaro. 

In either case, I would check their repective forums/wiki's.

---

### Post by su:bhatta on 2013-10-21
I am trying to resolve the problem through Manjaro forums. till now to no avail. 

Their only solution seems to be 'nomodeset', which I have tried. 
Thanks for the pointers am now looking at antergos forums too.

By  any chance do you also have my kind of hardware?

---

### Post by orb9220 on 2013-10-22
> **bhattabhishek said:**
> Thanks for the pointers am now looking at antergos forums too.
By  any chance do you also have my kind of hardware?

>  'Started GDM' & 'Target Reached Graphical Interface', but i am not getting a GUI.
The operation freezes in that CLI screen. 

Just downed Antergos today. 
And nope have completely different hardware than you. And still get the failed gnome LiveCD bootup problem like you.
This is not a specific hardware issue so much as a booting up the kernel with right grub params and boot script on the LiveCD.

They acknowledged there is an issue with it for many others.
Don't know about manjaro.
.

---

### Post by su:bhatta on 2013-10-22
> **orb9220 said:**
> Just downed Antergos today. 
And nope have completely different hardware than you. And still get the failed gnome LiveCD bootup problem like you.
This is not a specific hardware issue so much as a booting up the kernel with right grub params and boot script on the LiveCD.

They acknowledged there is an issue with it for many others.
Don't know about manjaro.
.

Yep, that is true! I tried to install Antergos in a different Laptop, and it gave same results. 

No resolution yet. Antergos Forum is also pretty crammed up place, there is one thread where everybody seems to post about there problem, which is the same one we faced.

Not upto mark yet I should say. 

Wanted to try Arch based something without the hassles of Arch installation. IMHO, Come on, I want a working machine, I ain't to understand workings and details of Linux codes. But whatever is needed to after the GUI comes up,  gotta know it.

---

### Post by BigSilly on 2013-10-26
> **bhattabhishek said:**
> Yep, that is true! I tried to install Antergos in a different Laptop, and it gave same results. 

No resolution yet. Antergos Forum is also pretty crammed up place, there is one thread where everybody seems to post about there problem, which is the same one we faced.

Not upto mark yet I should say. 

Wanted to try Arch based something without the hassles of Arch installation. IMHO, Come on, I want a working machine, I ain't to understand workings and details of Linux codes. But whatever is needed to after the GUI comes up,  gotta know it.

Exactly the same here guys. Have been trying to simply use the Antergos live disc to no avail. Tried the options offered on the forums but nothing would work.

As you say, I just wanted to try Arch but without the fight to install. There's definitely room for an Arch-based Gnome 3 distro, but Antergos seems a bit hit and miss. Or more miss for me. :D

---

### Post by kevdog on 2013-10-26
Nomodeset is a kernel directive.  I'm not sure if that really is your problem, however maybe trying to change kernel versions?

---

### Post by Allavona on 2013-10-26
Installing Arch is really not the headache its made out to be. Its rather straight forward.

Antergos: The gui installer has bugs obviously. Has anyone tried the command line installer yet? Same issue?

BridgeLinux also is Arch based and it has a Gnome 3 download available. But it has issues too. The autologin service persist into the new install and it loops the login over and over. alt+F2 can trick it into GDM and from there you can log in. If not you have to chroot into the install and manually stop the autologin and start getty.

ArchBang is an Openbox Arch based distro and as far as I know it works as advertized. Installing that and before doing anything else install Gnome 3.

     pacman -S gnome

     pacman -S gnome-extra

Then go grab a coffee.

With these distros, always do your research first. Both Arch and ArchBang have wikis. Just remember only use the Arch Forums for Arch. You go on there for Antergos or such your thread will be closed. But the wiki is fair game and can answer many of your questions for you.

---

### Post by su:bhatta on 2013-10-27
> **Allavona said:**
> Installing Arch is really not the headache its made out to be. Its rather straight forward.

Antergos: The gui installer has bugs obviously. Has anyone tried the command line installer yet? Same issue?

BridgeLinux also is Arch based and it has a Gnome 3 download available. But it has issues too. The autologin service persist into the new install and it loops the login over and over. alt+F2 can trick it into GDM and from there you can log in. If not you have to chroot into the install and manually stop the autologin and start getty.

ArchBang is an Openbox Arch based distro and as far as I know it works as advertized. Installing that and before doing anything else install Gnome 3.

     pacman -S gnome

     pacman -S gnome-extra

Then go grab a coffee.

With these distros, always do your research first. Both Arch and ArchBang have wikis. Just remember only use the Arch Forums for Arch. You go on there for Antergos or such your thread will be closed. But the wiki is fair game and can answer many of your questions for you.

@ Kevdog : Yes, nomodeset doesn't seem to the problem here. Looks like its some problem with the installation module.

@Allavona: I really don't want to mix 2 DE's. Always have had a bad experience when I have installed either KDE or Gnome on top of UbuntuStudio, which comes with stock Xfce.

& yes, I will read up Arch installation, if it's not a headache as you say, I am willing to get my hands dirty rather than having 2 DE's.

---

### Post by BigSilly on 2013-10-27
Well, I've downloaded the Arch iso, and installed Virtualbox on my current Ubuntu setup. For the amount of time spent trying to get easier Arch based distros going, I could have just opened up the Arch wiki and done it from scratch!

If it goes well I may switch to it, but I don't think I'll be removing my Ubuntu partition any time soon. ;)

---

### Post by kevdog on 2013-10-27
Arch isn't really all that much of a headache -- until it breaks with an upgrade and it takes the forums a few days to populate properly with an workable answer.  The Arch Linux beginner's install guide is great.  Please read the instructions a few time before beginning and if during the install something doesn't work or you don't understand the step -- you need to either google around or ask what the step means.  You can not skip steps unless they are not applicable to your hardware.  Good luck.  In a few hours you should be good to go -- it really doesn't take all that long. 

Off topic -- Gnome 3?  Each their own however I came to despise gnome 3. Recent upgrade within gnome 3 borked my entire system.  I eventually got that fixed and just switched to kde,  life has been much happier.

---

### Post by su:bhatta on 2013-10-27
> **kevdog said:**
> Arch isn't really all that much of a headache -- until it breaks with an upgrade and it takes the forums a few days to populate properly with an workable answer.  The Arch Linux beginner's install guide is great.  Please read the instructions a few time before beginning and if during the install something doesn't work or you don't understand the step -- you need to either google around or ask what the step means.  You can not skip steps unless they are not applicable to your hardware.  Good luck.  In a few hours you should be good to go -- it really doesn't take all that long. 

Off topic -- Gnome 3?  Each their own however I came to despise gnome 3. Recent upgrade within gnome 3 borked my entire system.  I eventually got that fixed and just switched to kde,  life has been much happier.

 I have a project to take printout of the Arch Guide & try it. But 'few hours' seems a little too much hassle & my hardware has proven to be kind of non-Linux friendly :( with Arch & Gentoo variants like Sabayon.

Also, these 3.10-3.11 kernels have heard to be a known issue with AMD GPU, 3.12 have heard to be more friendly.

Am currently running Ubuntu Gnome 13.10  with Gnome 3.10 & Ubuntu Studio Meta's added, which is proving to be a stable system for me, I for one ain't complaining. I like Gnome3 :)

 @BigSilly: No question of  removing Ubuntu partition, I ain't mad.

---

### Post by BigSilly on 2013-10-27
Right, spent a couple of hours typing today, trying to install Arch into a Vbox. Found a guide, and the Arch wiki, and gave it a go.

Geez the questions!

I made some balls up with it somewhere along the line, and ended up with an unbootable OS. Well done BigSilly. Living up to the name! Honestly, I think the issue was I skipped the creation of a /home partition, and I think I messed up doing that. Well, that and a bunchload of other stuff I probably didn't do right. :D

But at the end of the day, it's just not for me. Not that I couldn't do it if I had the time, but I guess that's exactly it. I don't have the time. I haven't got days to sit through all the finer points, I can't give it the time it would need in order to maintain it, and can't spare the time away from family cooped up in the basement hammering away at keys to end up with...! A working Linux that I could have gotten anywhere else.

I get why it has fans for sure (though I don't get why many of them have to look down on others), but right now I need an OS to be something that takes only a short while to install and maintain. I was impressed with the AUR very much though.

---

### Post by su:bhatta on 2013-10-27
> **BigSilly said:**
> 

But at the end of the day, it's just not for me. Not that I couldn't do it if I had the time, but I guess that's exactly it. I don't have the time. I haven't got days to sit through all the finer points, I can't give it the time it would need in order to maintain it, and can't spare the time away from family cooped up in the basement hammering away at keys to end up with...! A working Linux that I could have gotten anywhere else.

I get why it has fans for sure (though I don't get why many of them have to look down on others), but right now I need an OS to be something that takes only a short while to install and maintain. I was impressed with the AUR very much though.

My thinking exactly, & thats why i have been putting it off for 2 months ! maybe i never will try it or gentoo !

---

### Post by su:bhatta on 2013-10-30
I will mark this thread as Solved because Antergos seems to be a problem with many & Manjaro Forums have asked me to try out Manjaro default installation instead of ManjaroGnome and see if it works.

---

### Post by cecilpierce on 2013-11-21
I tried the Antergos 64 first with no luck, then the i686, same thing, finally did 'dd if=antergos-2013.11.17-i686.iso of=/dev/sdb' to a usb flash drive.

It booted up and I picked GUI installer, went well up to about 75% and screen froze but seemed to still be installing, waited til HD stopped and 

rebooted. It works but.... what a pain in the arch !!!

---

### Post by cecilpierce on 2013-11-22
Well I just tried it again with xfce4 and it installed all the way without screen freeze !

So now have 2 Antergos, 3 Manjaro an 1 Arch Linux working good...:D

---

