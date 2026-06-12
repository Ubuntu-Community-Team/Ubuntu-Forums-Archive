---
title: "No sound?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by spartanghost on 2007-11-06
Howdy folks. first timer here.  I just installed Ubuntu on my machine today and i'm already having a problem.  I bought a new toshiba a couple weeks ago ( Satellite A210-MS9 ) and i've got the OS running. Problem is, it doesnt detect any sound device!  The message it gives me when i click the speaker icon is 

"The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

it seems to me like my video card isn't installed.  My friend showed me how to get a list of the components, so here it is:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

so... anyone know what to do?  I'm a COMPLETE linux noob.  the lspci command is the most advanced thing i know how to do, so please put any answers in very simple terms. Thanks alot!

---

### Post by spartanghost on 2007-11-07
Would any more information be usefull?

---

### Post by Pumalite on 2007-11-07
Post:

sudo lshw -C sound

---

### Post by spartanghost on 2007-11-07
results of sudo  lshw -C sound:

 *-multimedia            
       description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

---

### Post by Pumalite on 2007-11-07
Good news. Your card is recognized and your kernel is loading the module.
These are some links that might help you:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by spartanghost on 2007-11-07
hmm those pages had alot of stuff on them and i have no idea what it means! I tried entering the code into the terminal from the second one but it just said 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

so... what should i do?  remember im a complete noob.  i need like, layman's layman's terms.

---

### Post by spartanghost on 2007-11-07
ok, well i tried method A on the first link and it diddnt work, so i tried Method B and it diddnt give me any errors, but the icon on the corner still shows the cross-out, and no sound is played.  there was a warning at the end of the last thing i did in the terminal that something was muted by default, but i cant access the volume control.  i'll try rebooting... but something tells me thats not gonna work.

---

