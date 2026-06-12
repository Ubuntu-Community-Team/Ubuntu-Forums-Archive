---
title: "How to connect to wireless network?(kubuntu 7.10)"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by joanaomgod on 2008-02-12
I have Kubuntu(on my laptop) and i want to connect to my wireless network at home. In windoze i enter a name of the network and a key.
My wireless adapter is Atheros

---

### Post by Het Irv on 2008-02-12
System-Administration-Network
Set you wireless to roaming mode
You should see a network icon in the top right by the clock
click on that and it should auto detect wireless networks in range.

Wireless has been a problem in the past with Ubuntu, and while it is better, it is not fully supported.  You may have to work with it a little to get it to work.  Post your wireless card's model if you have any problems

---

### Post by joanaomgod on 2008-02-12
I clicked on the icon, go to the options, but my network is not in trusted neither in untrusted sections...

---

### Post by Het Irv on 2008-02-12
Try clicking "Connect to Other Network"

Note: I am using Ubuntu (Gnome) I don't know how much the computer I am looking at and the computer you are looking at are the same.

---

### Post by joanaomgod on 2008-02-12
> **Het Irv said:**
> Try clicking "Connect to Other Network"

Note: I am using Ubuntu (Gnome) I don't know how much the computer I am looking at and the computer you are looking at are the same.

where is this button?

---

### Post by Het Irv on 2008-02-12
Doh' My bad.  I am looking in the wrong place.  Try right clicking on the Icon to see if wireless is enabled.  If it is and you cannot see any wireless connections, go back and uncheck roaming mode.  From there you should be able to put in your information.

Just out of Curiosity can you type ```
lspci
``` in the terminal and paste the output here.

---

### Post by Tuxoid on 2008-02-12
There should be an icon near your clock. It's a gear with a little bar or a wire with an x. Right-click on that, it should list any available network that are in-range. If you don't see a list of networks, make sure your wireless card is working. I'm sorry but I don't know how you test that without going through the CLI. Try searching "Help" under the K Menu for "ping", or "network". I assume you won't have to perform a ping at the command-line. Again, I'm sorry that I can only really point you to the documentation.

---

### Post by joanaomgod on 2008-02-12
Here it is what the console return from lspci: > 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

---

### Post by SandersOnSite on 2008-02-12
I setup my wireless recently, and it was really easy once I found 1 key piece of information.

Your SSID must be broadcasting on your access point. Or to put it another way it is not allowed to be hidden.

I had mine set to hidden, and no matter how many times I tried to "manually" configure my wireless on my laptop - it wouldnt connect untill I unhid it on the router.

J

---

### Post by clauguia on 2008-02-12
First of all, the driver to this chipset only works with Ubuntu 32bits version. It doesnt work wit 64bits in the time I write this message. So, if you have 64bits installed, download and install 32bits version (I have the two of them installed in different partitions, when I whant to go wireless, I boot the 32bits).

To install the driver to your Atheros AR5006EG, if you are in a Acer laptop, first install acer_acpi following this tutorial (this will enable your hardware button and other fancy stuff):

[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

Than install ndiswrapper either by synaptic or downlowding the last version from the official page (I use last version from official page, 1.52 and it does the magic for me).

The official page of ndiswrapper, where you can download the latest version:
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

To install the ndiswrapper from the page (tarball), you need to install from synaptic the package build-essential and follow this in  a terminal:
> 
$ tar xzf ndiswrapper-version.tar.gz
$ cd ndiswrapper-version/
$ make distclean
$ make
$ sudo make install

If you don&#8217;t need USB support in ndiswrapper, with recent versions, you can compile with make DISABLE_USB=1 and install with make DISABLE_USB=1 install (i didnt, though).

Now the driver, download it from the folowing site:

[http://www.atheros.cz/](http://www.atheros.cz/)

There is a table, click in the AR5006EG X XP32bits cell and download the topmost (last version). If this one doesnt work, you may try the AR5007EG driver, since its a reported bug to show wrongly in lspci as if it was 5006EG ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164984](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164984))
Unzip the driver and follow ndiswrapper instructions under "install windows driver":
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Thats it, you should be up and running.

---

