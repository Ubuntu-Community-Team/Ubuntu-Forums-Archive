---
title: "Dell wireless 1390 for 64 Feisty"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by cbivins on 2007-07-28
just got fiesty for a 64 bit system, and i am having problems with the system detecting my dell 1390 wireless card. i'm new to ubuntu, so i'm hoping someone can walk me through the process step-by-step. Thanks.

---

### Post by anewguy on 2007-07-28
Please click on Applications, then scroll down to Accesories then over to and click on terminal.

Type:  lspci

Then copy and post the output back here.  Maybe we can figure out what to do from there.:)

---

### Post by cbivins on 2007-07-28
chris@dhcppc1Earthlink:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
chris@dhcppc1Earthlink:~$

---

### Post by anewguy on 2007-07-28
Thanks for posting back that information.  The following line:

05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

tells us that your wireless card is based on a Broadcom chipset.

The already exists a how-to for this at:

[[COLOR="Red"]Click Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=297092")

After going through that how-to, if you still have problems then please re-post here and we'll see what we can do!:)

---

### Post by cbivins on 2007-07-28
Okay, now i feel really stupid. I went to the how-to for this and everything was going fine, and then after i pasted in the code for getting packages, i get a message that says 17.8mb of disk space will be used. do i want to continue [Y/n]?    No matter what i type (Y,y,yes, [Y], ect.) i get the message that says Abort. What am i supposed to be typing in to tell it i want to continue?

---

### Post by anewguy on 2007-07-28
Well, it should be just a "Y" followed by the enter key.  Click on "Places" and "Home Folder" and look at the bottom line on that window - it will say the free space of your disk.  Post that back here and we'll go from there.:)

---

### Post by anewguy on 2007-07-28
What's your status on this?:)

---

### Post by cbivins on 2007-07-28
I have 20.4 gb of free space so i don't think that is the problem. No matter what i do it still says abort. I thought maybe it was still working so i went on the next step and got the packages, uncompressed them and rebooted. After this the next step is to compile the program, but i'm a little confused about what is meant by "Now we'll complile the Ndiswrapper program. In a terminal, go to the directory where you extracted ndiswrapper and execute the following:

Code:

sudo make uninstall

"
am i supposed to be doing something other than pasting this code in a terminal? when i do that i get the message "make: *** No rule to make target `uninstall'.  Stop." Not sure if i'm making a mistake here or previous to this. Thanks for your help

---

### Post by anewguy on 2007-07-29
Instead of compiling ndiswrapper, try going into synaptics and installing it and ndiswrapper-utils, then try the ndiswrapper commands to load your driver.  You may want to see [[COLOR="MediumTurquoise"]this link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=507505") for an example of how I got wireless working with my 4318 adapter in my laptop.  Please post back with results and/or more questions.:)

---

### Post by cbivins on 2007-07-29
great idea about using synaptic to install ndiswrapper. That worked well and i'm currently loading the drivers from the dell website. Quick question though: how can i go to a directory while i'm in the terminal? Howto keeps saying In a terminal, go to the directory where you have the XXXXX file: what does that mean to go to the directory where a file is located while in a terminal? I can go to the file where it is located and i can open a terminal, but how do i open the directory from a terminal?

---

### Post by pissedoffdude on 2007-07-29
> **cbivins said:**
> great idea about using synaptic to install ndiswrapper. That worked well and i'm currently loading the drivers from the dell website. Quick question though: how can i go to a directory while i'm in the terminal? Howto keeps saying In a terminal, go to the directory where you have the XXXXX file: what does that mean to go to the directory where a file is located while in a terminal? I can go to the file where it is located and i can open a terminal, but how do i open the directory from a terminal?

To switch to the directory where you downloaded the file you will need to type "cd" in the terminal, for example if you downloaded the file to your desktop you would type ```
cd Desktop
```
If you downloaded the file your home folder then try ```
cd /home/*username* 
```

---

### Post by anewguy on 2007-07-29
How'd things work out for you?  I would be curious if everything worked out for you so we can point others with the same question to the answer!:)

---

