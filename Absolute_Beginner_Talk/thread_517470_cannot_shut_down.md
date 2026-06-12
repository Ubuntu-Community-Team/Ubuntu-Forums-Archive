---
title: "cannot shut down"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by nosh on 2007-08-04
When I try to shut down from ubuntu feisty, the screen turns black and I get the log of sound looping infinitely.  After this, I cannot boot normally: the screen turns black indefinitely after the ubuntu logo appears and the loading bar loads fully.  I can still boot into recovery mode, but I cannot shut down there either.  "shutdown now" gives a normal shutdown procedure, then freezes on "Sending all processes the TERM signal..."

This is a brand new install, dual booting with windows vista.  Vista still boots and shuts down perfectly.  Is there anything I can do to fix the ubuntu?

---

### Post by nosh on 2007-08-04
"shutdown -r now" works fine from within recovery mode, and now that I've done that once, "shutdown now" works as well and loads the root user.  But I still cannot boot normally.

---

### Post by dougfractal on 2007-08-04
more info please

touch post.log
lsb_release -a >post.log
uname -a >>post.log
dmesg >>post.log

cat  post.log

---

### Post by nosh on 2007-08-04
touch post.log
lsb_release -a >post.log
No LSB modules are available
uname -a >>post.log
dmesg >>post.log

[some is missing here, pg up/pg dn buttons have no effect and I don't know how else to get to it]

[     17.120000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[     17.388000] Linux agpgart interface v0.102 (c) Dave Jones
[     17.436000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[     17.436000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[     17.468000] input: PC Speaker as /class/input/input2
[     17.508000] sdhci: Secure Digital Host Controller Interface driver
[     17.508000] sdhci: Copyright(c) Pierrre Ossman
[     17.508000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[     17.508000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[     17.512000] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 7 (level, high) -> IRQ 7
[     17.512000] mmc0: SDHCI at 0xbc000800 irq 7 DMA
[     17.752000] ACPI: PCI Interrupt LInk [LAZA] enabled at IRQ 21
[     17.752000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 21 (level, high) -> IRQ 19
[     17.752000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[     17.924000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[     17.988000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[     18.180000] lp: driver loaded but no devices found
[     18.232000] Adding 2835432k swap on /dev/disk/by-uuid/50327460-ecad-4866-bdea-2402315b1f3.  Priority:-1 extents:1 across:2835432k
[     18.356000] EXT3 FS on sda3, internal journal

---

### Post by dougfractal on 2007-08-04
[some is missing here, pg up/pg dn buttons have no effect and I don't know how else to get to it]

either
mouse drag select and middle mouse button paste.
either gedit post.log copy/paste  into quotes
or 
attach post.log

---

### Post by nosh on 2007-08-04
Oh dear, this does not look good.  I've been trying different things, reconfiguring the xserver-xorg etc, in recovery mode and periodically trying out a normal boot to see if anything works.  I just got the standard "/dev/sda3 has been mounted 21 times without being checked, check forced."  Um, so the drive check has frozen at 23.6%.

This seems very bad. :shock:

Does this mean my hard drive is shot?  Or is linux just broken or what?  Please help

---

### Post by nosh on 2007-08-04
and now when I go to try booting in recovery mode (I got the earlier data from recovery mode, with no mouse or gedit to speak of, and no internet either) it forces a check again and this time freezes at 0.2% completion.

Please help!

---

### Post by lucy_liu_lover on 2007-08-04
I had a similar problem when I incorrectly edited the x-server config file. Ubuntu refused to boot. In order to restore the old config file I booted Ubuntu from the live CD. I then have access to the file system on the hard drive.

---

### Post by nosh on 2007-08-04
Unfortunately, this particular computer doesn't seem to want to boot from a live cd...
[http://ubuntuforums.org/showthread.php?p=3130191#post3130191](http://ubuntuforums.org/showthread.php?p=3130191#post3130191)

There is an option on the alternate cd to fix a broken installation, I'm thinking I might give that a shot...  But the weird thing is that I never touched the configure file before it crashed on the first shutdown.

---

### Post by lucy_liu_lover on 2007-08-04
Have you changed your BIOS settings so that  the CD drive as the first boot option ?

---

### Post by nosh on 2007-08-04
yes, everything runs fine from a live cd right up until it has to start the xserver, then it just freezes up.  Video card issue I think, nvidia.  Maybe not though.  But the text based installer works fine.

---

### Post by nosh on 2007-08-04
Okay, so I'm going to throw something out here.  During an ubuntu boot, and during the checking of sda3, I heard some small chirping from the hard drive.  It was small and high pitched, but it was definitely form the hard drive.  When I boot Vista, there is no sound from the hard drive whatsoever.  Is it possible that ubuntu's drivers for the hard drive are messed up (does a hard drive need drivers?).  What would possibly cause chirping when in linux but not when in windows?  Does anybody have any ideas?

---

### Post by dougfractal on 2007-08-05
3 things:  
1.xorg,  2. wireless card issuss, 3. acpi


**xorg**
[http://www.linuxmint.com/forum/viewtopic.php?t=3183](http://www.linuxmint.com/forum/viewtopic.php?t=3183)
> 
felixfurtak wrote:
Can report the following procedure works for Ubuntu Feisty 7.04 (final) live cd to at least boot into gnome:-

1. Boot CD as normal.
2. Select Safe Graphics Mode
3. Press F4 and Select 1024x768x16
4. Press F6 and remove options for quiet and splash
Eventually you get the X server fail to start and end up in the command prompt
5. Plug in your wired network connection (wireless may work, but didn´t for me since I have intel 4965agn - but that´s a different story) so that it can dhcp to your router
6. sudo apt-get install nvidia-glx
7. sudo nano /etc/X11/xorg.conf
8. In Section ¨Device¨ change ¨vesa¨ to ¨nvidia¨
9. CTRL-X to save
10. sudo /etc/init.d/gdm restart


**2.noapic **   at boot
```

acpi=off pci=noacpi pnpbios=off vga=0x317
```
> Adler

Has anyone tried to hit F6, and add "noapic" to the line that pops-up? That got me going with the last two Mint installs. I'm now on Cassandra, which rocks.


3.** wireless**
if you have a broadcom wireless this  might cause you problems

please post output
lspci -nn

---

### Post by nosh on 2007-08-06
how do I get dhcp to configure within a command prompt?  other then this, I think I'm getting everything working

---

### Post by nosh on 2007-08-06
alright, I got the liveboot cd booted up, and installed, and then I got the nvidia driver installed and reconfigured my xorg so all is good so far (thank you all very much for your help!).  Still need to get the wireless working though, so here is the requested output:

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

---

### Post by dougfractal on 2007-08-06
> 03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)

try here 
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)


good luck
Doug

---

### Post by nosh on 2007-08-06
Yes!  everything works! my faith in ubuntu is restored.  Thank you very much, and keep up the good work.

---

