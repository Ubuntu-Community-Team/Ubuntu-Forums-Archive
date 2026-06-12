---
title: "A series of unfortunate events..."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Inkubas on 2007-03-24
Hello everyone. Let me first compliment the moderators and the helpful community of individuals I see before me. This is the first forum I've seen with such a great deal of devotion. I'm impressed. And I hope that you can help me , bear with my stupid/noob questions and ,point me in the right directions.

My problem stems from the fact that I've been forced fed Windows all my life. I never liked Macs, and Linux was new to me till a few years ago when I was first introduced into Red Hat then Fedora then Mindriva(I believe). After a series of head aches and someone the mercy to direct me to Ubuntu. Let me tell you guys, I was so shocked at how much help there is and how easy it was to install/configure a great deal of my system. Wow...that's all I can really say...ok anyway, I can sit here with my mouth open all day but I've got some problems. I'll state the first one. For some reason there's a problem with shutting down the computer. It seems that it takes so long to shut down no matter if I shut down through the terminal or if I shut down by clicking on the shut down icon on the upper right side of my screen. Furthermore, I like a great deal of people here seem to have a problem configuring/installing the correct network drivers. So if you can kindly direct me to the right direction on a REAL newbie answer on the matter, I'd greatly appricate it I'm not exactly sure how to find out the specs on my system.OH..at the moment. My keyboard is doing strange things like moving minimizing/maximizing windows and before it was moving my cursor left/right. Is this a bug or idiocy on my part? By the way, I'm sorry for the disorder of my questions/comments it's been a long day. Any and all help is appreciated .

---

### Post by old_geekster on 2007-03-24
Welcome to Ubuntu and to the forum!

I have been using Edgy for approximately a month.  I can't believe that you can find this kind of quality for free.  What a bargin.

Here is a guide that will help you considerably:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28xine-ui.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28xine-ui.29)

It will give you assistance on simply everything.

To answer your questions, it would help to know what components you have in your rig.  Also, the type of keyboard that you have would help.

If your rig is older, Edgy will have more difficulty correctly installing the components.  It is as the name (Edgy) implies, on the cutting-edge.

To find the specs of your rig, you can install AID32, Everest Home Edition, or Sandra.  Any one of these will give you everything that you want to know.  I am not sure if there is a Linux version for any of these, but you can use a XP version.

Oh, by the way, there are no stupid newbie questions on this forum.  The only stupid question is the one you didn't ask.  Everyone of us is/was a newbie in the beginning.

---

### Post by sad_iq on 2007-03-24
Try **lspci** in a terminal...that should give you something about your hardware(there are more commands...but can't remember yet...It's too early...have to drink my coffee first)!!!
 About your keyboard ...I have the same problem but with my mouse...it really goes crazy sometimes(random clicks, deleting stuff, closing apps)...it appears to be the cable...I'll buy a new one when I'll have the time!!!

---

### Post by Inkubas on 2007-03-24
Thanks for the start. Ok, I'm awake right now. I've got an HP pavilion Intel Dual Centrino dv100 laptop model.
I believe that I'm running "Edgy EEt 6.10 Ubuntu"

***************************************************************************************
A more detailed version of my specs are as follows:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
**************************************************************************************

There are three main areas of my concern which include  the hardware issues that I'm receiving with my Wifi connection, **occasionally** random keyboard and mouse and configuring my screen resolution to something other then the 1024 *768.

My second area of my concern is the fact that I don't know what I need in order to fix these issues.

The third is that this is a bit over my head. I'm still on the windows withdraw phase here. I'll admit, I'm used to just point click enter a name done applications/software.
I've noticed that with Linux you've got to download the code and compile it following the instructions. When I tried to follow the instructions I'd inevitably receive an error.

For example, I noticed that I needed a Linux-based driver for my network card. I searched it up and found it on the HP website. After I downloaded it and all the other software needed I tried follow the installation instructions step by step but despite my most valiant of efforts I would fall short either in finding the data, creating a make file, or running the script. (I did all those under the root-user alias with the password). I can't remember the exact code and I can't write too much at the moment since I've got to get ready for work. But I believe I would get error 1 or 2. "Permission denied"  "Cannot create <file name>".

However, through this all there's some hope! I did manage to install/upload ndisksw (I believe that's the utility) so now I've got a graphical interface for the Wifi. The only problem is that it shows my modem/ethernet/wireless but I still need to install a correct driver for the wireless (inf file) which I can't seem to find. It just tells me that I've got ipw3945 and that there's "Hardware Present: No"

Thank you. I'll check back on this forum as well as read the guide you've given me the moment I get back from work.

---

### Post by halitech on 2007-03-24
this one is your wireless card

```

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

and it is supported but Intel hasn't released totally free drivers so you also need to download the binary driver from Intel, then as sudo, copy the files to 

```

/sys/firmware

```

then reboot and you should be connected. more info here [http://ipw3945.sourceforge.net/]("http://ipw3945.sourceforge.net/")

edit: original location was wrong, has been corrected now

---

### Post by Inkubas on 2007-03-25
Thanks for the help. I followed the links and downloaded everything you specified. However, when I compiled everything I didn't see any files or directories copied into the firmware folder. I'm not even sure what a binary file looks like. I did, however, follow the instructions and compiled both the ieee subsystem, the daemon, and the drivers. I'm going to reboot and post if it works. If not then I'll have to work on it some more tonight.

By the way, thanks for the help. The instructions are clear and well written. I really appreciate the help.

---

### Post by halitech on 2007-03-25
I don't have a wireless cazrd so I'm not sure and just going on memory from a Linux Reality podcast where they spoke about the intel wireless cards and what I found on the intel website. I'm not sure if the binary file is .bin or not. I was hoping there was better info in the download instructions. 

Hope it worked.

---

### Post by Inkubas on 2007-03-25
Ok, this is a bit strange. Now the flashing light for my wireless is off completely. Before it would blink on and off. And I'm still not getting any driver working or anything to show up on the "Windows Wireless Driver" in system...

I'm going to take a break from problem A. At the moment, I can use the Ethernet connection. However, I've got a far more annoying problem. My keyboard randomly goes crazy. While I'm typing it would randomly change position to a left or right alignment. If I'm typing something in terminal it would minimize the window I'm working on and select another window.

---

### Post by Inkubas on 2007-03-28
Ok, I'm stumped. I tried to build up the driver from the Install. I compiled the ipw395, ipw395d, ipw395.ucode and the deamon. I installed them into the /lib/firmware folder and STILL no result. Whenever I try to see if there is even a driver present there's no "Hardware" in the System> Admin > Windows Wireless driver. 

Anyone have any other ideas? Is it possible that I've done something wrong or missed something?

On a side note. I've still got a problem with my keyboard. At times there's not a single thing wrong with it. But sometimes, for no apperent reason, it seems to just delete, shift location, or minimize the window I'm working on.
Anyone know any way to fix this? I'm afraid to do something that'd mess up my keyboard driver.

---

