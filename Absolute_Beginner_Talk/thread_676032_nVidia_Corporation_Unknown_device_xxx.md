---
title: "nVidia Corporation Unknown device xxx"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Cal55 on 2008-01-23
I'm trying to resolve a sound issue on my newly-installed Gutsy install on a PC with an MSI P6NGM / MS-7366 mainboard.  When I do 'lspci' many devices report 'nVidia Corporation Unknown device xxx'.  Thus :-
```
00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```
The VGA controller (a PCI-E card) was only recognised once I disabled the on-board graphics in BIOS.

Thus.  Are these ...Unknown device statements problematic?  

Is this highlighting a basic problem with the mainboard, or at least it's detection by Ubuntu?

I'm really not experienced with Linux or in-depth computer hardware.  However,  I suspect the problem might lie with the fact that my PC has an MSI P6NGM mainboard.  This apparently has an nVidia MCP73U/PV/V chipset (whatever that is).  Is this not supported by Ubuntu/Linux?  Is it likely ever to be?

Any help much appreciated.

Chris

---

### Post by Paulmd on 2008-01-24
> **Cal55 said:**
> I'm trying to resolve a sound issue on my newly-installed Gutsy install on a PC with an MSI P6NGM / MS-7366 mainboard.  When I do 'lspci' many devices report 'nVidia Corporation Unknown device xxx'.  Thus :-
```
00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```
The VGA controller (a PCI-E card) was only recognised once I disabled the on-board graphics in BIOS.

Thus.  Are these ...Unknown device statements problematic?  

Is this highlighting a basic problem with the mainboard, or at least it's detection by Ubuntu?

I'm really not experienced with Linux or in-depth computer hardware.  However,  I suspect the problem might lie with the fact that my PC has an MSI P6NGM mainboard.  This apparently has an nVidia MCP73U/PV/V chipset (whatever that is).  Is this not supported by Ubuntu/Linux?  Is it likely ever to be?

Any help much appreciated.

Chris


NVIDIA nForce Drivers

Open source drivers for NVIDIA nForce hardware are included in the standard Linux kernel and leading Linux distributions. This page includes information on open source drivers, and driver disks for older Linux distributions including 32-bit and 64-bit versions of Linux. 
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Linux nForce Drivers

All of the following drivers are open-source and are included in most popular Linux distributions. In most cases, the Linux installer will select the appropriate driver for the detected nForce hardware. 

[http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

---

### Post by Cal55 on 2008-01-24
Thanks Paulmd.  

If I understand your links correctly, the assumption is that drivers for NFORCE devices ought to be in the kernel?

I think the problem is that the NFORCE-MCP73 is fairly new, and so hasn't hit Ubuntu yet.  Having said that, I've just tried the Alpha of 8.04 and didn't get any further.  lspci still shows many 'nVidia Corporation Unknown device' statements.  The /var/log/messages file shows lots of references to NFORCE-MCP73 however.  Must back-level to 7.10 now to compare...

Is there any way to find out what kernel version will support the MCP73 chipset?

Cheers
Chris

---

### Post by overdrank on 2008-01-24
> **Cal55 said:**
> Thanks Paulmd.  

If I understand your links correctly, the assumption is that drivers for NFORCE devices ought to be in the kernel?

I think the problem is that the NFORCE-MCP73 is fairly new, and so hasn't hit Ubuntu yet.  Having said that, I've just tried the Alpha of 8.04 and didn't get any further.  lspci still shows many 'nVidia Corporation Unknown device' statements.  The /var/log/messages file shows lots of references to NFORCE-MCP73 however.  Must back-level to 7.10 now to compare...

Is there any way to find out what kernel version will support the MCP73 chipset?

Cheers
Chris

HI and you may try this command to update your pci ids ```
sudo update-pciids
```

---

### Post by Paulmd on 2008-01-25
> **Cal55 said:**
> Thanks Paulmd.  

If I understand your links correctly, the assumption is that drivers for NFORCE devices ought to be in the kernel?

I think the problem is that the NFORCE-MCP73 is fairly new, and so hasn't hit Ubuntu yet.  Having said that, I've just tried the Alpha of 8.04 and didn't get any further.  lspci still shows many 'nVidia Corporation Unknown device' statements.  The /var/log/messages file shows lots of references to NFORCE-MCP73 however.  Must back-level to 7.10 now to compare...

Is there any way to find out what kernel version will support the MCP73 chipset?

Cheers
Chris

I did a bit more digging. Nvidia hosts a peer-support forum SPECIFICALLY for linux support of their products. 

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

This is a "sticky" on that forum.
[http://www.nvnews.net/vbulletin/showthread.php?t=73925](http://www.nvnews.net/vbulletin/showthread.php?t=73925)


It may be worth a visit.

---

### Post by Cal55 on 2008-01-25
Hi overdrank.  

> **overdrank said:**
> HI and you may try this command to update your pci ids ```
sudo update-pciids
```

It looks like the pci ids for my devices are not yet listed, part under review.  I'll keep an eye on the list and update when available.  

Do I take it then that the descriptions given by 'lspci' are purely cosmetic?  Or does the fact that a device description is unknown suggest that it might not be performing correctly?

Many thanks.

Chris

---

### Post by Cal55 on 2008-01-25
Thanks Paulmd.  The forum looks useful.

I've checked the listed Nvidia modules with lsmod and most seem to be loaded so things should be ok. 

Thanks 
Chris

---

### Post by Paulmd on 2008-01-26
> **Cal55 said:**
> Hi overdrank.  



It looks like the pci ids for my devices are not yet listed, part under review.  I'll keep an eye on the list and update when available.  

Do I take it then that the descriptions given by 'lspci' are purely cosmetic?  Or does the fact that a device description is unknown suggest that it might not be performing correctly?

Many thanks.

Chris

In Windows, having an "unknown device" in the device manager is a bad thing. In Ubuntu, at least, it's ambiguous. It's one thing Microsoft does better. Their device manager actually manages devices. (Ubuntu has GOT to do this better)

---

### Post by Cal55 on 2008-01-27
Thanks Paulmd,

I would tend to agree.  Looking at 'HAL Device Manager 0.5.9.1' under System/Preferences/Hardware Information hasn't been too useful.  It just lists the 'unknown device'(s) but gives no clue as to whether they're functioning correctly or at all.  In fact, I've found the gui version of lshw  : lshw-gtk rather more useful as at least it attempt to relate devices to modules (which I assume are drivers...)

When I've HAD to fix a Win-based PC I've found Device Manager flagging devices not performing/recognised quite helpful, as well as the information on the date of the driver used.

Still trying to work out if I really have problems (other than non-functional on-board sound, which I could live with)

I also have to admit to being a bit mystified by how this all works and why I can't get a sensible overview.  As for example at boot linux kernel seems for example to detect my IDE controller correctly :-```
Jan 26 18:11:16 dev-pc kernel: [   20.325073] NFORCE-MCP73: IDE controller at PCI slot 0000:00:08.0
``` (from /var/log/messages)

But lspci reports ```
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)

```

HAL Device Manager gives it as : Vendor:nVidia Corporation. Device:Unknown (0x056c)

lshw-gtk gives it as: Vendor:nVidia Corporation.  product:nVidia Corporation.  bus info: pci@0000:00:08.0.  But does at least give - driver:AMD_IDE and module:amd74xx.



Cheers
Chris

---

