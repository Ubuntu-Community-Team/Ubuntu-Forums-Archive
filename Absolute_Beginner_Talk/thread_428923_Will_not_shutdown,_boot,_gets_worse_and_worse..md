---
title: "Will not shutdown, boot, gets worse and worse."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by kordite on 2007-04-30
This is an extremely long story that I will boil down to its essentials. 

Have an IBM T-20 laptop, Win98. Installed 6.06. No problems except that I couldn't get the wireless card to connect to the network. Did troubleshooting with someone online. He suggested I upgrade. I upgraded to 6.10 and then to 7.04. Suddenly the screen resolution was only 800x600. Also wouldn't shut down properly. Didn't like booting up either. Troubleshooting with forums failed to resolve issue. 

FDISK and start a clean install of 7.04. Screen OK but still not shutting down or booting right. Still network card issue. Figured the wireless issue was less important then not being able to boot so wipde the drive and tried installing 6.06 clean again. The shutdown and reboot issue is getting worse. 

Now even the boot from the install disk is having problems. Will take two or three reboots to come up. I can go through an install but it won't shut down. It will reboot once to do the updates but won't boot after that.

First question: could there be something left on the drive that even an FDISK /MBR won't wipe out? 

I am very new to Ubuntu and Linux but have been Windows support and corporate level help desk (1st and 2nd level) for a long time, so I know generally what I'm doing with a PC.

---

### Post by bobbybobington on 2007-04-30
:-k  strange... IBM's generally work w/ linux really well. I don't know how old it is (just guessing from the win98) if so you may want to look into xubuntu. Perhaps acpi is giving you grief. :confused:

---

### Post by starcraft.man on 2007-04-30
Well, assuming that each time you did a wipe you removed all partitions and redid them or at least formatted all the partitions when overwriting them then I highly doubt that this is a problem with software. I mean if 6.06 never gave you trouble and after you wiped the drive and put it back it has boot problems, it sounds to me like its not software related.

So, since it is not likely software after all those installs and formats, I'd say it may be a safe bet that some part of the hardware is failing. Most problems start to become apparent when mobo goes, might be that. Don't know if there is a way to know for sure without replacing parts >.>.

---

### Post by apunc1 on 2007-04-30
acpi could very well be the booting/fail to shutdown problem. i have an older machine that does this and still fails to shutdown completely in xubuntu.

here is something you may want to try to turn off acpi
[http://ubuntuforums.org/showpost.php?p=9953&postcount=3](http://ubuntuforums.org/showpost.php?p=9953&postcount=3)

as for the network card, that is also a documented problem. there are some possible solutions here [http://ubuntuforums.org/showthread.php?t=122415](http://ubuntuforums.org/showthread.php?t=122415) but unfortunately the network cards on IBM T-20 are very problematic with linux

good luck

---

### Post by kordite on 2007-05-01
> as for the network card

Actually, the internal network card works without issue. It was the wireless card I was having problems with (Orinoco Silver PCMCIA). It worked fine when I was using Win98, that is, until my wife monkeyed with it. You see, when I first got the card, it worked fine. My daughter needed a wireless card for her laptop so I gave her mine and got another one for myself. That card didn't work in my PC so I installed it in my daughter's and it was ok. But my original card no longer worked in my unit. It took a long time and numerous calls to support to finally work through that. Then, we got a second AP and my card wouldn't connect to it. My wife did troubleshooting but only succeeded in getting it so my card wouldn't connect to the original AP. I couldn't figure that out so I finally said "to hell with windows drivers", wiped it and tried Ubuntu.

A sad story but only peripheral to the PC not booting now. I tend to doubt it being a hardware issue as it worked previously without issue. It worked after installing 6.06 without issue. It's onl;y after the update that things went bad and have been going worse. Some specifics about it's "not booting": I get the Ubuntu splash screen, it goes through the load with the status bar (or the script if in 6.06), and then at the point where one might expect the login prompt i get a blank screen with a flashing cursor. The cursor then stops flashing and that's it.

When this problem first started, I would reboot and it would come up. Another install and it would take 3 or 4 reboots for it to finally come up. Now, any number of reboots do not come up. 

Hardware? I'm not convinced by that unless Ubuntu is doing something to an EPROM or the BIOS. I've read a few forum postings about something like that but I'm not familiar enough to troubleshoot that yet. I do have an older BIOS and have been trying to update that but the install utility only runs with windows. I tried re-installing windows but have been having difficulty. I could get 95 to install but it wouldn't run the patch. I couldn't get it to upgrade to 98. I'm looking to borrow some 2K disks to try that.

I';m not quite ready to give up on this PC yet but Dell just announced that they are going to be selling at least one model of the E-series laptops pre-installed with the latest version of Ubuntu at the end of the month. [http://www.theregister.co.uk/2007/05/01/dell_linux_lives/]("http://www.theregister.co.uk/2007/05/01/dell_linux_lives/") In the meantime I'll try some of the troubleshooting suggested above (once I get home).

---

