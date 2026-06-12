---
title: "Madwifi/wireless help"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2006-01-31
I'm having trouble compiling the madwifi driver for my Airlink DWL-G630 wireless card.  Following the instructions under [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo), their guide to installing it I have problems with the make command.  When I type in make I get the error message:
Makefile.inc:94: Default KERNELPATH not found, using /usr/src/linux
Makefile.inc:104: *** KERNELPATH: /usr/src/linux does not exist.  Stop.
I have no idea what's going on and any help would be much appreciated.

---

### Post by madddonkey255 on 2006-02-01
Anyone have any ideas?

---

### Post by moopere on 2006-02-01
[QUOTE=madddonkey255]Anyone have any ideas?[/QUOTE]

I never had any luck at all compiling the MADWIFI stuff.  Always seemed to me that it was made for a redhat (or similar) system and a stock Debian install is just different enough to cause problems.

I gave up in the end when I discovered Ubuntu which had madwifi included (restricted module) and now my wireless 'just works' - is there any reason why your atheros wifi card needs to have madwifi compiled?  

Cheers,
Craig

---

### Post by madddonkey255 on 2006-02-01
For some reason the driver for my card wasn't installed or something.  Through a fluke or something the card isn't detected, it worked in windows fine before I switched to ubuntu so I'm guessing it's madwifi.

---

### Post by henshu70 on 2006-02-02
Hi there. My computer is Toshiba Satellite P20. When I installed Ubuntu 5.10 at first the wireless device was detected correctly. Than I reinstalled the NVIDIA driver and it was just gone. After some search I found this very useful HOW TO on installing the madwifi drivers. Thought it may be helpful here:

[HOWTO: Latest madwifi svn snapshot]("http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi+ng")

---

### Post by madddonkey255 on 2006-02-02
When I try to do that I get the error message
E: Couldn't find package linux-headers-uname -r

---

### Post by moopere on 2006-02-02
[QUOTE=madddonkey255]For some reason the driver for my card wasn't installed or something.  Through a fluke or something the card isn't detected, it worked in windows fine before I switched to ubuntu so I'm guessing it's madwifi.[/QUOTE]

Whats an 'lspci' from the command line give you?  I'd be pretty surprised if the linux-restricted-modules package to suit your kernel didn't already have a working atheros module.

I guess its possible that hotplug is not picking it up though - lets have a look at lspci then I'll try and walk you through it (as I have a Dlink atheros card in my notebook here).

Cheers,
Craig

---

### Post by madddonkey255 on 2006-02-02
When I lspci I get:
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go 5200] (rev a1)
0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

---

### Post by moopere on 2006-02-03
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

That will be the problem right there - your wireless card is not atheros based so madwifi won't work.

I have no clue as to whether any sort of driver exists for this Marvel chip, their website might have some answers or perhaps a quick google on "marvel 8300 linux" might turn something up.

Cheers,
Craig

---

### Post by Lambert on 2006-02-03
[QUOTE=madddonkey255]When I try to do that I get the error message
E: Couldn't find package linux-headers-uname -r[/QUOTE]

it should look like this.

sudo apt-get install linux-headers-`uname -r`

Notice the ` before and after the uname -r. This is important because the package is not called this it's actually linx-headers-2.6.12-10-386 or something like this. What the `uname -r` part does is import the actual kernel you're running in to that part of the command so you get the correct headers for the kernel version you're running. If you know what kernel you're running you can replace the `uname -r` part with the actual kernel version. of course to get that information you just run uname -r in a terminal.

Note that is a backtick not a single quote. It's found on a us keyboard next to the 1 above the tab key.

And moopere is correct, I don't see an atheros device in your output.

---

### Post by madddonkey255 on 2006-02-03
Thanks for all the help.  I went to the wireless database ([https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards))
and found something I didn't notice before I guess, it says "Works in Breezy (just configure it from the gnome network config tool), though it isn't recognized durring installation"  I went to Network tools under system tools and didn't see anywhere where I could configure it, it only had ethernet and loopback.  None of the other applications in my menus allow me to configure a wireless card and I was just wondering where that gnome network config tool was.

Thanks,
Nolan

---

### Post by madddonkey255 on 2006-02-04
I've been looking for somewhere to configure my wireless card and while looking at a help I saw that I don't have an Add feature for Connections in the Network Settings.  I've only got Properties, Activate, and Deactivate.  I'm not sure if there is something I need to add-on to that so that I can add my wireless or if I'm even looking at the right thing.  
Thanks,
Nolan

---

### Post by moopere on 2006-02-07
[QUOTE=madddonkey255]I've been looking for somewhere to configure my wireless card and while looking at a help I saw that I don't have an Add feature for Connections in the Network Settings.  I've only got Properties, Activate, and Deactivate.  I'm not sure if there is something I need to add-on to that so that I can add my wireless or if I'm even looking at the right thing.  
Thanks,
Nolan[/QUOTE]

Well, I had a look at the link you provided above - it appears that there are at least 3 different G630's mentioned and they also appear to have different chipsets (as I alluded to earlier).  If you are referring to this one:

"Works in Breezy (just configure it from the gnome network config tool), though it isn't recognized durring installation. Works only via ndiswrapper in Warty and Hoary."

This comment doesn't tell me anything about Breezy, it may be that the comment was posted when hoary was current - so, its probable then that you'll need to use ndiswrapper to get the driver loaded.

Once the driver is loaded you will need to use the network config tool that you are currently staring at in order to set up the card for IP address etc etc.  Note that the network config tool won't help you at all to install a driver.

I'd start getting to the bottom of this one by checking what card you actually have (Rev A, B, C, D or E) as they are all based on different chipsets and what you do next will be determined by the chipset used.  

Its almost a  given that whatever chipset is being used is not 'out of box' supported by Ubuntu or else hotplug would most likely have picked it up by now - you will probably need to use ndiswrapper.

Cheers,
Craig

---

