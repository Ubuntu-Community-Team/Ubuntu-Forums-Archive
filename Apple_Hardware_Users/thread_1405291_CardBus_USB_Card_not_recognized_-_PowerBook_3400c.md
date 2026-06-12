---
title: "CardBus USB Card not recognized - PowerBook 3400c"
date: 2010-02-12
forum: Apple Hardware Users
---

### Post by sopranojam85 on 2010-02-12
Hello everyone,

I have a Good Way Technologies BU2220 CardBus USB 2.0 card which works fine on this same Mac under OS 9.1. It also works fine on a more modern mac with OS X. But I cannot understand why it's not working in Ubuntu 9.10.

I had it recognized (I think??) when I had Kubuntu 5.10  (Breezy Badger) installed on this system.

I have an old dog - a PowerBook 3400c 240 Mhz 80MB Ram, with a 40 GB HDD. I have Mac OS 9.1 installed on a 5GB partition, and the rest is Ubuntu 9.10, using the LXDE GUI. I switch between Mac OS and Linux using Boot X.

When I slide in my USB card (making sure I have the external power supply attached to it), the system shows a bit of activity, and my display brightness reverts to default. Then there's no more activity. Of course, USB flash drives and USB mice won't work when plugged in.

I navigated to /var/log, and looked in the Messages log. There were the following entries:

Feb 11 13:42:09 PowerBook kernel: [  374.949456] pcmcia_socket pcmcia_socket1: pccard: CardBus card inserted into slot 1
Feb 11 13:42:09 PowerBook kernel: [  374.949881] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot
Feb 11 13:42:09 PowerBook kernel: [  374.949916] pci 0000:05:00.0: PME# disabled
Feb 11 13:42:09 PowerBook kernel: [  374.950212] pci 0000:05:00.1: PME# supported from D0 D1 D2 D3hot
Feb 11 13:42:09 PowerBook kernel: [  374.950243] pci 0000:05:00.1: PME# disabled
Feb 11 13:42:09 PowerBook kernel: [  374.950541] pci 0000:05:00.2: PME# supported from D0 D1 D2 D3hot
Feb 11 13:42:09 PowerBook kernel: [  374.950573] pci 0000:05:00.2: PME# disabled
Feb 11 13:42:09 PowerBook kernel: [  374.951643] ohci_hcd 0000:05:00.0: enabling device (0000 -> 0002)
Feb 11 13:42:09 PowerBook kernel: [  374.951879] ohci_hcd 0000:05:00.0: OHCI Host Controller
Feb 11 13:42:09 PowerBook kernel: [  374.952800] ohci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 1
Feb 11 13:42:09 PowerBook kernel: [  374.953717] Oops: Exception in kernel mode, sig: 5 [#1]
Feb 11 13:42:09 PowerBook kernel: [  374.953743] PowerMac
Feb 11 13:42:09 PowerBook kernel: [  374.953759] Modules linked in: uinput ipv6 snd_powermac snd_pcm snd_timer snd soundcore iptable_filter nls_utf8 snd_page_alloc ip_tables hfsplus pcmcia x_tables yenta_socket pmac_zilog loop uninorth_agp rsrc_nonstatic serial_core evdev apm_emu rtc_generic agpgart pcmcia_core apm_emulation windfarm_core mesh de2104x
Feb 11 13:42:09 PowerBook kernel: [  374.954021] NIP: c03482a8 LR: c0329a60 CTR: c034431c
Feb 11 13:42:09 PowerBook kernel: [  374.954058] REGS: c3b59d00 TRAP: 0700   Not tainted  (2.6.31-14-powerpc)
Feb 11 13:42:09 PowerBook kernel: [  374.954084] MSR: 00029032 <EE,ME,CE,IR,DR>  CR: 22000028  XER: 20000000
Feb 11 13:42:09 PowerBook kernel: [  374.954157] TASK = c3735be0[491] 'pccardd' THREAD: c3b58000
Feb 11 13:42:09 PowerBook kernel: [  374.954181] GPR00: 00000001 c3b59db0 c3735be0 c2cfac58 c2cfac00 00000000 00000001 00000001 
Feb 11 13:42:09 PowerBook kernel: [  374.954246] GPR08: 00000020 00000000 00000000 00000140 22000044 00dd60a8 00000000 00000000 
Feb 11 13:42:09 PowerBook kernel: [  374.954308] GPR16: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000 
Feb 11 13:42:09 PowerBook kernel: [  374.954370] GPR24: 00000000 c05c3778 00000002 00000000 000000a0 c2c78400 c2c78c00 c2c78ce8 
Feb 11 13:42:09 PowerBook kernel: [  374.954499] NIP [c03482a8] ohci_init+0x2cc/0x408
Feb 11 13:42:09 PowerBook kernel: [  374.954540] LR [c0329a60] usb_add_hcd+0x144/0x404
Feb 11 13:42:09 PowerBook kernel: [  374.954563] Call Trace:
Feb 11 13:42:09 PowerBook kernel: [  374.954636] [c3b59db0] [c05c3778] iomem_resource+0x0/0x1c (unreliable)
Feb 11 13:42:09 PowerBook kernel: [  374.954683] [c3b59dd0] [c0329a60] usb_add_hcd+0x144/0x404
Feb 11 13:42:09 PowerBook kernel: [  374.954728] [c3b59df0] [c03384d8] usb_hcd_pci_probe+0x1dc/0x29c
Feb 11 13:42:09 PowerBook kernel: [  374.954783] [c3b59e20] [c0247740] local_pci_probe+0x24/0x34
Feb 11 13:42:09 PowerBook kernel: [  374.954832] [c3b59e30] [c0248a60] pci_device_probe+0x84/0xa8
Feb 11 13:42:09 PowerBook kernel: [  374.954882] [c3b59e60] [c02c541c] really_probe+0x74/0x198
Feb 11 13:42:09 PowerBook kernel: [  374.954924] [c3b59e80] [c02c47bc] bus_for_each_drv+0x70/0xac
Feb 11 13:42:09 PowerBook kernel: [  374.954966] [c3b59eb0] [c02c5758] device_attach+0x84/0xa8
Feb 11 13:42:09 PowerBook kernel: [  374.955007] [c3b59ed0] [c02c3fe0] bus_probe_device+0x2c/0x44
Feb 11 13:42:09 PowerBook kernel: [  374.955081] [c3b59ee0] [c02c2a44] device_add+0x2c8/0x3d8
Feb 11 13:42:09 PowerBook kernel: [  374.955157] [c3b59f20] [c0241a40] pci_bus_add_device+0x1c/0x5c
Feb 11 13:42:09 PowerBook kernel: [  374.955202] [c3b59f30] [c0241ad8] pci_bus_add_devices+0x58/0x174
Feb 11 13:42:09 PowerBook kernel: [  374.955376] [c3b59f50] [c643c00c] cb_alloc+0xe4/0x628 [pcmcia_core]
Feb 11 13:42:10 PowerBook kernel: [  374.955459] [c3b59f70] [c64379c0] socket_insert+0xe8/0x114 [pcmcia_core]
Feb 11 13:42:10 PowerBook kernel: [  374.955545] [c3b59f80] [c6438494] pccardd+0x240/0x2a4 [pcmcia_core]
Feb 11 13:42:10 PowerBook kernel: [  374.955606] [c3b59fc0] [c005c38c] kthread+0x78/0x7c
Feb 11 13:42:10 PowerBook kernel: [  374.955658] [c3b59ff0] [c001646c] kernel_thread+0x4c/0x68
Feb 11 13:42:10 PowerBook kernel: [  374.955685] Instruction dump:
Feb 11 13:42:10 PowerBook kernel: [  374.955709] 80090004 0c000000 4c00012c 4bfffdcc 807fff18 38000001 39200000 2f830000 
Feb 11 13:42:10 PowerBook kernel: [  374.955772] 419e0010 81230084 7d200034 5400d97e <0f000000> 80090000 38800100 38bf0008 
Feb 11 13:42:10 PowerBook kernel: [  374.955854] ---[ end trace bf75035cd8174769 ]---


I'm a bit clueless where to go from here. It seems like other folks report success with this same model card on Ubuntu 9.10. Any help would be very much appreciated.

---

### Post by linuxopjemac on 2010-02-13
give me the output of 
```
sudo lspci -v
```

---

### Post by sopranojam85 on 2010-02-17
[SIZE=4]**Output without card connected:**[/SIZE]


00:0b.0 Host bridge: Apple Computer Inc. Bandit PowerPC host bridge (rev 03)
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Kernel modules: uninorth-agp

00:0d.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
    Flags: bus master, medium devsel, latency 32, IRQ 60
    I/O ports at 0400 [size=128]
    Memory at 80802000 (32-bit, non-prefetchable) [size=128]
    Expansion ROM at 80880000 [disabled] [size=256K]
    Kernel driver in use: de2104x
    Kernel modules: de2104x

00:0e.0 Class ff00: Apple Computer Inc. O'Hare I/O (rev 01)
    Flags: bus master, medium devsel, latency 32, IRQ 28
    Memory at 80900000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

00:10.0 Class ff00: Apple Computer Inc. O'Hare I/O (rev 01)
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at f3000000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

00:11.0 VGA compatible controller: Chips and Technologies F65550 (rev 45)
    Flags: stepping, medium devsel, IRQ 24
    Memory at 81000000 (32-bit, non-prefetchable) [size=16M]
    Expansion ROM at 80840000 [disabled] [size=256K]
    Kernel driver in use: chipsfb

00:13.0 CardBus bridge: Texas Instruments PCI1130 (rev 04)
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at 80804000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
    Memory window 0: 84000000-87fff000 (prefetchable)
    Memory window 1: 88000000-8bfff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001100-000011ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

00:13.1 CardBus bridge: Texas Instruments PCI1130 (rev 04)
    Flags: bus master, medium devsel, latency 168, IRQ 23
    Memory at 80803000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
    Memory window 0: 8c000000-8ffff000 (prefetchable)
    Memory window 1: 90000000-93fff000
    I/O window 0: 00001200-000012ff
    I/O window 1: 00001300-000013ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket


[SIZE=4]
**Output WITH card connected:**[/SIZE]

pcilib: Cannot open /sys/bus/pci/devices/0000:01:00.0/config
lspci: Unable to read the standard configuration space header of device 0000:01:00.0
00:0b.0 Host bridge: Apple Computer Inc. Bandit PowerPC host bridge (rev 03)
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Kernel modules: uninorth-agp

00:0d.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
    Flags: bus master, medium devsel, latency 32, IRQ 60
    I/O ports at 0400 [size=128]
    Memory at 80802000 (32-bit, non-prefetchable) [size=128]
    Expansion ROM at 80880000 [disabled] [size=256K]
    Kernel driver in use: de2104x
    Kernel modules: de2104x

00:0e.0 Class ff00: Apple Computer Inc. O'Hare I/O (rev 01)
    Flags: bus master, medium devsel, latency 32, IRQ 28
    Memory at 80900000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

00:10.0 Class ff00: Apple Computer Inc. O'Hare I/O (rev 01)
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at f3000000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

00:11.0 VGA compatible controller: Chips and Technologies F65550 (rev 45)
    Flags: stepping, medium devsel, IRQ 24
    Memory at 81000000 (32-bit, non-prefetchable) [size=16M]
    Expansion ROM at 80840000 [disabled] [size=256K]
    Kernel driver in use: chipsfb

00:13.0 CardBus bridge: Texas Instruments PCI1130 (rev 04)
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at 80804000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
    Memory window 0: 84000000-87fff000 (prefetchable)
    Memory window 1: 88000000-8bfff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001100-000011ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

00:13.1 CardBus bridge: Texas Instruments PCI1130 (rev 04)
    Flags: bus master, medium devsel, latency 168, IRQ 23
    Memory at 80803000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
    Memory window 0: 8c000000-8ffff000 (prefetchable)
    Memory window 1: 90000000-93fff000
    I/O window 0: 00001200-000012ff
    I/O window 1: 00001300-000013ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

---

### Post by linuxopjemac on 2010-02-17
I have no idea what to do, I can't see any clue where to start. Can you plug it into an Intel PC and see if it is recognized ? Maybe with the name of the device as it is recognized by the kernel, you can look up the module/driver for it. Then you can look if you can port that to powerpc.

---

### Post by sopranojam85 on 2010-02-17
The lspci output shows only this for the card:

Cannot open /sys/bus/pci/devices/0000:01:00.0/config
lspci: Unable to read the standard configuration space header of device 0000:01:00.0


Out of curiosity, I navigated to this folder path. When I went to /sys/bus/pci/devices, there were icons for folders, but they appeared to be aliases to other folders. The 0000:01:00.0 folder had several files in it, but did not have the file called "config." Also, all of the content of this folder had a net size of 0 kb. ......(confused??)

I tried making a blank text file called "config" and saving it to the 0000:01:00.0 folder, but I kept getting errors that the file path was invalid.

I don't know much about these files or folders......other than I guess that these files somehow relate to bus devices.

The Messages.log file said:

Modules linked in: uinput ipv6 snd_powermac snd_pcm snd_timer snd soundcore iptable_filter nls_utf8 snd_page_alloc ip_tables hfsplus pcmcia x_tables yenta_socket pmac_zilog loop uninorth_agp rsrc_nonstatic serial_core evdev apm_emu rtc_generic agpgart pcmcia_core apm_emulation windfarm_core mesh de2104x

What does this mean? Does this mean that the system is trying to load all of those drivers, with no luck?

---

### Post by linuxopjemac on 2010-02-18
I guess that those modules are associated with the devices which are found with the lspci command.

---

### Post by sopranojam85 on 2010-03-30
I'm giving this thread a bump.

Anyone have any more clues about this issue?

I'm puzzled by this line:

```
Cannot open /sys/bus/pci/devices/0000:01:00.0/config
lspci: Unable to read the standard configuration space header of device 0000:01:00.0
```

Anyone know what that directory does and how to manipulate it?

---

### Post by PowerbookVirg on 2010-04-27
I've encountered the same problem with my PowerBook Wallstreet, and upon some investigation I think I know why it's a problem.  Of course, I'm not sure how to fix it yet, but I'll toss out my ideas and hope that others might be able to add to them.

I have a CompUSA USB 2.0 CardBus PC Card Adapter and a Dell TrueMobile 1300 wireless card (based on the Broadcom 4300 chipset).  My PC cards both worked under Debian Etch on the same laptop a few days ago, and they both appear in OS9.2.2 (although the TrueMobile doesn't work).  I installed Ubuntu 9.10 but had several problems getting it to work.  It would not properly load the Mach64 ATI driver for video, so I was stuck with the FBDev basic framebuffer video driver, which looked awful.  Because of this I switched to XUbuntu 9.10 installed from the alternate CD (BootX was already installed and working for Debian so I just had to switch the kernels/RAMdrive images around).  Now the video looks great and the rest of the hardware is acting normally.

However, LSPCI now reports pretty much the same error as reported in the original post.  Based on some digging, my suspicion is that the change from pcmcia-cs to pcmciautils (and the switch to using hotplug to access the pcmcia drivers) is why it won't work now.  For right now, I have no clue how to confirm this, but I'm going to try to dig my way back through pcmcis-cs stuff to see if there are any ways to get it working under the new pcmcia programming.

One other point to note (which may help the experts) is that X will not load if I boot the machine with a card installed.  It reports that the video driver is not PCI, and won't start until I reboot without the card inserted.  lspci shows the line...

00:11.0 Display Controller: ATI Technologies Inc 3D Rage LT Pro (rev dc)

...but startx crashes until the whole thing is restarted without the card.  Inserting the card after the system is up and running does not crash X but of course the card doesn't work.

I'll come back as I discover more, but if anyone can take this suspicion and turn it into a working configuration I'd truly appreciate it.

sopranojam85, the line you're questioning is a device line.  The directory is populated by the system when a card is inserted (and it starts correctly).  The reason you can't touch it is because it doesn't actually exist until there's a card installed and working in the slot (the "files" are just stubs until the card starts which is why they're all zero bytes).  Because the pcmcia system can't get the card started, the directory doesn't get populated by the manager.  If you could manipulate that directory or the config file, you wouldn't need to be here since it would be working.

Virg

---

### Post by PowerbookVirg on 2010-04-27
Returning with more to add.

I just inserted a SanDisk 32MB (woohoo!) PCMCIA mass storage card.  It didn't prevent X from working correctly, LSPCI doesn't throw any errors, pccardctl info shows:

PRODID_1="SunDisk"
PRODID_2="SDP"
PRODID_3="5/3 0.6"
PRODID_4=""
MANFID=0045,0401
FUNCID=4
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

pccardctl status shows:

Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "pata_pcmcia"

...and I can access the filesystem on the card.  So, a 16 bit card seems to have no trouble (as I suspected) but 32-bit cards still don't work.  This seems like more evidence that it's the change from pcmcia_cs to udev that's causing the issue.

More as I find it.

Edited to add: Inserting the CompUSA USB card changes Socket 1 from "no card" to "3,3V 32-bit PC Card" so the system is recognizing that a CardBus card has been inserted at least.

Virg

---

### Post by PowerbookVirg on 2010-04-28
O.  M.  G.

Here's the latest.  I inserted the USB card into slot 0, and got the same stuff as I always did.  I checked /var/log/messages and saw the same stuff that sopranojam85 saw.  I checked lspci and saw the usual failure.

Now here's the fun part.  I physically removed the USB card, and then inserted my Dell TrueMobile 1300 wireless network card into slot 1.  I figured to see the errors for the other slot to look for differences.  Well, the major difference I found is that the card started.

I have installed the bcom4300-fwcutter package for the card and inserted "pci=noacpi" into my boot perameters in BootX.  

The long and short of it is that I got the drivers properly configured for the WLAN card and it stopped crashing the bus.  So now, I'm down to the same situation that sopranojam85 sees, in that I can't get my USB adapter to work correctly.

Something that I discovered as I was digging is that the machine I'm using has a built in USB host controller.  The problem is that there's no external access to it (no USB ports and nowhere to connect a wire or anything) so I still need the CardBus adapter installed.  I'm going to investigate disabling the system's discovery and access to the internal USB in the hopes that it will allow installation of the external, but if I'm barking up the wrong tree here please let me know.

Virg

---

### Post by PowerbookVirg on 2010-05-05
I've solved the problem.

I installed 10.04 Lucid Lynx cold from the PPC alternate CD.   I wiped out my 9.10 installation and reformatted the drive partition.   I put xubuntu-desktop in place because the gnome desktop is more than my Wallstreet can easily handle, but when I finished, I simply hotplugged my CompUSA USB card and it worked correctly.   I rebooted and made sure that they coldplugged as well.  I've gotten all of the other doodads that I need installed, and it's running like a champ.   It's not fast, but it's working.   Lucid managed to configure pbbuttonsd, the proper ATI driver and ALSA for the Powermac Screamer without intervention.   The only problem I've encountered so far is that I'm unable to adjust the screen resolution from 1024x768@30Hz.   This is the best native resolution, though, and it's got at least 16 thousand colors so it looks fine for now.   I'll dig around in xorg.conf to see if I can solve it, but it works as it stands so I'll consider it a win.

As a note to complete my other posts, I also removed "pc=noacpi" from my boot parameters in BootX, since that was an attempt to deal with the problem in 9.10.

Virg

---

### Post by linuxopjemac on 2010-05-05
I would advize you to switch to LXDE
```

sudo apt-get install lubuntu-desktop
```

Then next time you login from gdm, choose lxde as session. It's much faster than XFCE.

---

### Post by sopranojam85 on 2010-08-26
Good stuff!

Well I'm glad that 10.04 at least works with your setup. I'm having a problem with my system not recognizing the 10.04 CD after I burn it. It's too large so I have to overburn it in OS X Terminal. From there it mounts fine on OS X, but for some reason my PowerBook 3400c won't mount the disk in OS 9 and fusses to eject it.

Anyway I'll play with this more later. For now, good to know that 10.04 may be the solution.

---

### Post by sopranojam85 on 2011-03-24
No luck installing 10.04, or 10.10. Various installation issues here, mostly chalked up to my antiquated hardware.

I know Breezy Badger (5.10) recognized my USB card.

Ubuntu 9.10 would install OK but would not recognize my card.

Trying to find a happy medium. Installing 8.04.1 (Hardy Heron) PPC alternate, will post my results.

---

### Post by sopranojam85 on 2011-03-25
Yup, 8.04.1 worked like a charm, recognizes the card right away. I'm sticking with that version, given that it seems to be the latest, fully functional version I can put on this old dog.

---

