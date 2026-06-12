---
title: "First day in linux..."
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by vip on 2006-10-23
Hey all,

I just installed a mobile rack into my Dell this past weekend and I figured, why not install Ubuntu?  I ordered a Live CD a couple months back and was planning on turning an old computer into a Linux box, but since all the parts are still laying around, I might as well try it out on a computer I have up and running.  

I have both a hard drive and a DVD-RW hooked up as cable select on the secondary IDE channel.  Here are the specs of my computer:

Dimension 3000
Processor: Intel® Pentium® 4 Processor (2.80GHz, 533 FSB)
Memory:	512MB Dual Channel 400MHz DDR SDRAM
Video Card: Integrated Intel® Extreme Graphics 2
Network Interface: Integrated 10/100 Ethernet
Sound Card: Sound Blaster® Live! 24-bit ADVANCED HD Audio
DVD+/-RW: 16x NEC ND-3520A

As you can see, pretty run-of-the-mill specs straight from the factory.  There is an 80GB hard drive installed on the primary IDE channel as master which I am running XP SP2 off of, but that doesn't matter anyways since I am keeping both OS's on separate HDs.  The HD in the mobile rack which I installed Ubuntu on is an older Maxtor 90845D4 8.4GB, just enough for the OS and to put on some basic applications.

Ubuntu installed w/o a hitch, although I did not like the GRUB boot loader that it installed on my computer because it would give me problems when I switched out the Ubuntu HD with a regular NTFS-formatted one that I am using for backing up my XP stuff.   I fixed this by booting into the Recovery Console from the WinXP CD and doing the "fixmbr" command.

I have yet to get sound working on the Sound Blaster Live! card, and wireless networking seems to not be working also.  Plugging in the cable and using the integrated 10/100 port works fine though, which I guess is good.  The card I am using is an AirLink+ ([http://airlinkplus.com/wireless/awlh3025.htm)](http://airlinkplus.com/wireless/awlh3025.htm)), although I am unsure of the exact model number, that link was the only PCI card I could find on their site.  I used the lspci command in the Terminal and it seems to be returning a Texas Instruments ACX 111 chipset.  I will paste the actual lines returned later when I get to my house.  Anyway, my network is running WPA-PSK so I made sure that wpa_supplicant was installed, then I downloaded network-manager, and also ndiswrapper.  I downloaded the driver package off of the AirLink+ site and unzipped it to a folder on my desktop.  I used Ndiswrapper to install the Windows drivers for my wireless adapter (tnet1130.inf) and Ndiswrapper said that my Hardware was present.

I went into the Network and disabled my eth0 connection and unplugged my cable.  I then enabled the wlan0 connection and left the key blank (at this point I turned off all wireless security on my router just to see if I could connect).  No go so far.  I gave up after a couple hours last night and I will try again once I go home.  Just to cover my bases, I wanna ensure everybody that I went step-by-step through the instructions in this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

And still no go.  I'm curious as to if it has really detected my wireless adapter or not, Ndiswrapper says my hardware is present yet I cannot connect to the internet at all.  The network manager icon is also not showing up in the corner at all.  Is it supposed to show up when I am connected to wired internet also?

Anyways, this is my progress up until now, I'm here at work right now so I can't work on anything until I get home.  Just want to verify that my network does work; I can boot into Windows XP immediately after and connect to the net using wireless.  I am not concerned with the WPA at this moment because whenever I try to connect to wireless in Ubuntu I turn off all wireless security.  Only once I connect to wireless will I worry about the WPA details.

So, to recap I have installed:
network manager
wpa_supplicant (for future usage)
ndiswrapper-utils
ndisgtk (GUI for ndiswrapper)

I'm not sure if I should have installed anything else... I don't even think I dl'd wpa supplicant, I think it was already installed during the basic install from the Live CD. 

Oh, and the contents of the driver zip package from AirLink+ are still sitting in a folder on my desktop, I was unsure if I could delete them after installing them through Ndiswrapper.  That's all folks, will be back with updates.

---

### Post by Malakia on 2006-10-23
Make sure that it says driver present to when you do ndiswrapper -l if it doesn't try going to the ndiswrapper website and find your card their and use the driver they have listed for your card. If that doesn't work than compile ndiswrapper from source and see if that works.

---

