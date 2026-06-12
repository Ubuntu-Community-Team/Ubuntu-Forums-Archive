---
title: "Help! how to install hardware drivers?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by cheapos on 2006-07-30
Hi, I'm a complete noob. Just installed Ubuntu for 64bit amd today and was trying to install the drivers for all my hardware as below:
Netgear pci wireless card
creative audigy 2
Nvidia Geforce 7300
LG LCD monitor 

They all come with cds of their own and none installed when i try to install them. I can see the soundcard and the nvidia on the device manager so assume they can be used. 

I websearched everywhere on my xp computer for help as my ubuntu one can't get on the internet w/o the wireless card. Seems like the solution is to find alternative drivers online and also to type codes to install. But I don't even know where and how i can get to the place to type the code?
Need help desperately...
F

---

### Post by dmizer on 2006-07-30
well then ... let's get you online first.  i'm sure someone will come along with some nvidia know how, but i believe it amounts to patching the kernel ... (please don't quote me on that).

okay ... start by posting the output of: lspci iwconfig and ifconfig

open a terminal and type:
```
lspci >> lotsofinfo.txt
ifconfig >> lotsofinfo.txt
iwconfig >> lotsofinfo.txt
```
then use whatever media available to transfer the "lotsofinfo.txt" file from your ubuntu computer to your connected windows computer. eg: usb drive.

edit: sorry, i had to edit that one.  i shouldn't be posting so late at night ... lol.

---

### Post by cheapos on 2006-07-30
Thanks for the reply! 
This is what it gave me, so how do I continue?

Thanks,
F

-v              Be verbose
-n              Show numeric ID's
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-s [[<bus>]:][<slot>][.[<func>]]        Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-X              Show in format suitable for use in XFree86Config
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

---

### Post by mrbig1492 on 2008-02-28
It looks like all you got was the option list for the command, " lspci"

You should have seen something like:
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

So it seems like your lspci command failed for some reason and you are getting a mini help file to try and tell you the correct format for the command.

I don't know much else, but hopefully that will point you on your way a little further.

E

---

