---
title: "Formatting a Disk: NTSC, FAT, FAT32"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Firi on 2007-12-19
I plan to install Ubuntu 7.10 on a Dell XPS M140 and I have a few questions about formatting.  I'm following this eHow.com guide...

[http://www.ehow.com/how_6026_format-hard-drive.html](http://www.ehow.com/how_6026_format-hard-drive.html)

...And at Step 5 it states to delete partitions and such.  I have three partitions: FAT, FAT32, and NTFS.  I know almost nothing about partitions and what they do, but I understand that NTFS is the main C: drive.  So, I'm wondering a few things before I delete things:

1. What is FAT and FAT32?

2. Can FAT and FAT32 be formatted?  Do I need to?  If so, can they be replaced if I somehow need them in the future?

3. Can I combine FAT, FAT32, and NTFS into one, whole "partition" and install Ubuntu to that?  (If so, what does this mean in terms of functionality, exactly?)

When I right-click FAT, the only option is "Help," but FAT32 has a "Delete Partition" option as the eHow guide mentions.  Should I delete this partition?

I plan to completely replace Windows XP Professional SP2 with Ubuntu 7.10 (no dual-booting or anything for now, at least).  I need internet access with a connection over a home network via a router as well as remote printing (using this laptop to send print jobs over the home network).  I also send files to and from another PC (with Windows XP Home) over the network.  I'm unsure if any of this is relevant to FAT, FAT32, partitions, and so forth, but I thought I'd add the information, anyway.

I guess I basically need to know how to properly format my disk with FAT, FAT32, and NTFS involved in relation to Ubuntu (and home networking).  I do not want to accidentally erase something that I need for Ubuntu and so forth.

Thanks.

EDIT:  The title should read NTFS, not NTSC.  Ha ha...

---

### Post by RomeReactor on 2007-12-19
Hi. [FAT]("http://en.wikipedia.org/wiki/File_Allocation_Table") and [NTFS]("http://en.wikipedia.org/wiki/Ntfs") are file systems; if you plan on using only Ubuntu on that computer, then the installer will automatically erase the existing partitions and create the necessary [EXT3]("http://en.wikipedia.org/wiki/Ext3") partitions for Ubuntu, so there's no need to do that yourself.

---

### Post by Sef on 2007-12-19
First, have you run the live cd to make sure everything works?

Sedond, questions:

> 1. What is FAT and FAT32?

2. Can FAT and FAT32 be formatted? Do I need to? If so, can they be replaced if I somehow need them in the future?

3. Can I combine FAT, FAT32, and NTFS into one, whole "partition" and install Ubuntu to that? (If so, what does this mean in terms of functionality, exactly?)


1) They are file systems for Windows.

2) Yes, you should format them as ext3 since you are not dual booting.

3) Yes, you can.  You should have 3 partitions: / (root), /home, and /swap.

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing") for more information.

---

### Post by shadow-of-sin on 2007-12-19
Also do not delete any partition without backing up your data first, I recommend backing up everything you need before installing Ubuntu. If you're going to completely replace Windows then you wont have to do anything to your FAT32 partitions- you can just reformat the NTFS Windows partition to EXT3 with the livecd installer(remember that all data is lost when formatting so backup!)

---

### Post by wjp.reg on 2007-12-19
> First, have you run the live cd to make sure everything works?

I would think this would be your first step before you make any changes to your system, so that you can determine that all the hardware components work or will work after installing specific drivers.

Should you choose to recover Windows at a later date, you need to either have a recovery disk (from Dell), or a recovery partition left intact on the computer from which you could boot and restore.

M2CW :-)

---

### Post by zvacet on 2007-12-19
First of all you don´t want to format NTFS because that is your WinOS.Now

1.[Read this](http://en.wikipedia.org/wiki/Fat32)

2.Yes and I don´t know.If you need extra free space then yes,but be sure to backup anything you don´t want to lose from these partitions.

3.No,Ubuntu use ext3 format.

And now I see that you plan to delete windows completly.Once again if  you have any files or data that you want to backup do it.after that you can install ubuntu and during the partition it will ask you how do you like to partition your Hd.On that step you can delete all partitions.More [here](http://www.psychocats.net/ubuntu/installing).

---

### Post by Firi on 2007-12-19
> **RomeReactor said:**
> Hi. [FAT]("http://en.wikipedia.org/wiki/File_Allocation_Table") and [NTFS]("http://en.wikipedia.org/wiki/Ntfs") are file systems; if you plan on using only Ubuntu on that computer, then the installer will automatically erase the existing partitions and create the necessary [EXT3]("http://en.wikipedia.org/wiki/Ext3") partitions for Ubuntu, so there's no need to do that yourself.

So, I don't need to format anything?  Or should I still format the NTFS partition?

---

### Post by RomeReactor on 2007-12-19
If you plan on using the entire hard drive for Ubuntu, no, you don't need to, Ubuntu will do it for you. But you should follow the advice of everyone here and back up **any and all** important information you have on that drive, since telling Ubuntu to use the entire disk will obviously erase everything there and format the drive to use the EXT3 filesystem. Follow the [tutorial posted by zvacet]("http://www.psychocats.net/ubuntu/installing"), and when you reach the partitioner choose **Guided - use entire disk**.

---

### Post by Firi on 2007-12-19
> **RomeReactor said:**
> If you plan on using the entire hard drive for Ubuntu, no, you don't need to. But you should follow the advice of everyone here and back up **any and all** important information you have on that drive, since telling Ubuntu to use the entire disk will obviously erase everything there and format the drive to use the EXT3 filesystem.

I don't know what's on FAT and FAT32, though.  I didn't even know that they existed until a few hours ago.  If there's important information on them, I don't know how to access it, nor do I know how to back it up.  I have already backed up everything that I wish to keep on the NTFS partition, however.

---

### Post by RomeReactor on 2007-12-19
Can you post a screenshot of the step where it shows you the three partitions? one of the FAT partitions is probably swap.

---

### Post by Firi on 2007-12-19
> **RomeReactor said:**
> Can you post a screenshot of the step where it shows you the three partitions? one of the FAT partitions is probably swap.

Sure.

---

### Post by RomeReactor on 2007-12-19
It looks like the the 3.61 GB partition is the swap; the 39 MB one is a utility partition; more on that [here]("http://www.duxcw.com/yabbse/index.php?board=5;action=display;threadid=628").

Just in case, if you didn't create that 3.61GB partition (and therefore you didn't put any information there yourself), and no one else uses that computer (so no one else would have any information stored there), and if you've already backed up all your important information, then I would say it's fairly safe to install Ubuntu there, which will format the whole disk and create new partitions.

However, you should try Ubuntu before installing it, so you can see if you like the OS, and to check for hardware that doesn't work "out of the box". I suggest you try Ubuntu for at least a week using it in Live CD mode (which will **not** touch your hard drive and won't install anything until you tell it to) so get to know its interface before deciding to install it permanently.

---

### Post by Firi on 2007-12-19
> **RomeReactor said:**
> It looks like the the 3.61 GB partition is the swap; the 39 MB one is a utility partition; more on that [here]("http://www.duxcw.com/yabbse/index.php?board=5;action=display;threadid=628").

Just in case, if you didn't create that 3.61GB partition (and therefore you didn't put any information there yourself), and no one else uses that computer (so no one else would have any information stored there), and if you've already backed up all your important information, then I would say it's fairly safe to install Ubuntu there, which will format the whole disk and create new partitions.

However, you should try Ubuntu before installing it, so you can see if you like the OS, and to check for hardware that doesn't work "out of the box". I suggest you try Ubuntu for at least a week using it in Live CD mode (which will **not** touch your hard drive and won't install anything until you tell it to) so get to know its interface before deciding to install it permanently.


I didn't create the FAT, FAT32, nor NTFS partitions.  I assume they were always there in the background.

Is Live CD mode on the Ubuntu 7.10 i386 disc?  I didn't see it.  Is it in the "Start or Install Ubuntu" option?

Also, I am using this laptop: [http://www.notebookreview.com/assets/8294.jpg](http://www.notebookreview.com/assets/8294.jpg) and I am wondering what will become of the media buttons (Play, Stop, Pause, Next, Volume Up, et cetera) that you see on the front (below the touchpad buttons).  Will they be useless on Ubuntu, or will Ubuntu recognize them?  Also, when XP Pro is gone, what will happen to functions such as making the screen brighter or dimmer with "Fn + Up/Down"?  How about the Windows logo key?  Ha ha.  Will these questions be answered on the Live CD?

---

### Post by RomeReactor on 2007-12-19
Yes, the "Start or Install Ubuntu" is the Live CD mode. As for the multimedia buttons, most of the time Ubuntu just configures them correctly, so when you get to your desktop you'll probably be able to use them. If they don't work, it probably means that it needs to install packages not found in the CD, and for that it needs to be installed; otherwise, if you install any packages while running in Live CD (yes, it can be done), the packages are stored in your system's RAM, and they'll be gone once you shut down Ubuntu. Just remember that not everything might work in Live CD, but most--if not all--of those things can be made to work once the system is installed.

As a side note, a very useful thing to do when running the Live Cd is to open a terminal, located in "Applications->Accessories->Terminal", and writing or pasting the following command:
```
lspci
```
and pressing ENTER. If something doesn't work in Live CD it is possible that it could be a tricky bit of hardware to get working even after Ubuntu is installed, and posting the results of the **lspci** command will let people know what hardware your laptop has, so they'll be able to help you better with troubleshooting. Antoher useful command is:
```
sudo lshw
```

As for dimming or brightening the screen, I can't help you there since I don't have a laptop, but maybe it's accomplished the same way; other people will be able to answer that question. And the windows key will work, but it will do different things.

---

### Post by Firi on 2007-12-19
> **RomeReactor said:**
> Yes, the "Start or Install Ubuntu" is the Live CD mode. As for the multimedia buttons, most of the time Ubuntu just configures them correctly, so when you get to your desktop you'll probably be able to use them. If they don't work, it probably means that it need to install packages not found in the CD, and for that it needs to be installed; otherwise, if you install any packages while running in Live CD (yes, it can be done), the packages are stored in your system's RAM, and they'll be gone once you shut down Ubuntu. Just remember that not everything might work in Live CD, but most--if not all--of those things can be made to work once the system is installed.

As a side note, a very useful thing to do when running the Live Cd is to open a terminal, located in "Applications->Accessories->Terminal", and writing or pasting the following command:
```
lspci
```
and pressing ENTER. If something doesn't work in Live CD it is possible that it could be a tricky bit of hardware to get working even after Ubuntu is installed, and posting the results of the **lspci** command will let people know what hardware your laptop has, so they'll be able to help you better with troubleshooting.



All right, thanks for the help.  Here's what I've gathered:

- Because neither I nor anyone I know created the FAT and FAT32 partitions, their content is most likely unimportant and not worth backing up.  (If it is worth backing up, I'm still unsure how to actually access the information on them.)
- I don't actually need to manually format NTFS, FAT, nor FAT32 because the Ubuntu installation will erase everything for me and create the appropriate Ubuntu partitions.
- Use Live CD for approximately a week before installing/erasing anything.

Please correct me if I'm wrong.

---

### Post by shadow-of-sin on 2007-12-19
> **Firi said:**
> All right, thanks for the help.  Here's what I've gathered:

- Because neither I nor anyone I know created the FAT and FAT32 partitions, their content is most likely unimportant and not worth backing up.  (If it is worth backing up, I'm still unsure how to actually access the information on them.)
- I don't actually need to manually format NTFS, FAT, nor FAT32 because the Ubuntu installation will erase everything for me and create the appropriate Ubuntu partitions.
- Use Live CD for approximately a week before installing/erasing anything.

Please correct me if I'm wrong.
Yeah that's right. The FAT/FAT32 partitions are just the recovery partitions that your laptop manufacturer has created in case you want to reinstall Windows XP (most laptops come with "Recovery CDs" which can be used in conjunction with the recovery partitions for a new XP installation). You don't **have** to use the Live CD for 1 whole week- just make sure all your hardware is working and that you're ready to make the switch to linux.

---

### Post by RomeReactor on 2007-12-19
> **Firi said:**
> All right, thanks for the help.  Here's what I've gathered:

- Because neither I nor anyone I know created the FAT and FAT32 partitions, their content is most likely unimportant and not worth backing up.  (If it is worth backing up, I'm still unsure how to actually access the information on them.)
The 3.61 GB partition is most likely the swap, so it doesn't contain any user data; the 39 MB partition was put there by whatever OEM sold you that laptop, and it contains configuration files relating to the hardware, not user data.


> - I don't actually need to manually format NTFS, FAT, nor FAT32 because the Ubuntu installation will erase everything for me and create the appropriate Ubuntu partitions.
That's correct.

> - Use Live CD for approximately a week before installing/erasing anything.
That is just an estimate; it's up to you to decide when you're comfortable enough with Ubuntu to go ahead with the installation, but yes, I do recommend you spend at least a few days getting to know the system and its way of doing things.

You'll see an **Install Ubuntu** icon on the desktop; **don't** use it unless you want to permanently install Ubuntu. When you want to shut down Ubuntu, press the button (upper right corner of the screen) in the attached screenshot.

---

### Post by Firi on 2007-12-19
All right, I'm on the Live CD now, and I have two main questions:

1. The Bluetooth LED light on the laptop (beside Caps Lock, Num Lock, et cetera) constantly blinks.  While it is a nice shade of blue, the constant blinking is annoying.  I've fiddled around with the Bluetooth settings a bit, but I can't figure out how to turn Bluetooth off and/or stop the blinking light.

2.  I entered both "lspci" and "sudo lshw" into the Terminal, and got the following, so... what does this mean exactly?  Is there something for which I should be looking?

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Portable Computer
    product: MXC051
    vendor: Dell Inc.
    serial: 58J5591
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-3800-104A-8035-B5C04F353931
  *-core
       description: Motherboard
       product: 0HC416
       vendor: Dell Inc.
       physical id: 0
       serial: .58J5591.CN7016661100TP.
       slot: @
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A02 (11/06/2005)
          size: 64KB
          capacity: 512KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1867MHz
          capacity: 1867MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KB
             capacity: 8KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: AD00000000000000
             physical id: 0
             serial: 00005073
             slot: DIMM_A
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: AD00000000000000
             physical id: 1
             serial: 00007075
             slot: DIMM_B
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:14:22:96:20:8e
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:02:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@0000:02:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2915ABG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:d4:d9:3d
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.100 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: Hitachi HTS72106
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MC3O
                serial: MPC3B2Y3G9AY5E
                size: 54GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Dell Utility partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 39MB
                   capabilities: primary
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 50GB
                   capabilities: primary bootable
              *-volume:2
                   description: CP/M / CTOS / ... partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 3702MB
                   capabilities: primary
           *-cdrom
                description: DVD writer
                product: DVD+-RW DW-Q58A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UDS1
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
  *-battery
       product: DELL C95535C
       vendor: SMP-SDI2.4
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V

---

### Post by RomeReactor on 2007-12-19
I don't have Bluetooth, so someone else will likely be able to help you with that.

As for the commands, they list the hardware components of your laptop:

* lspci = list PCI devices
* lshw = list hardware
* lsusb = list USB devices

They are useful to know what hardaware the machine has; in **lspci**, you can see:

* VGA compatible controller = video card (integrated or other).
* Audio device = sound card (integrated or other).
* Ethernet controller = your ethermnet/LAN port.
* Network controller = your wireless card.

As you can see, the results for **lshw** were much more detailed, so to avoid clutter people might want you to run it with a few parameters; for example:
```
sudo lshw -C display
```
to list *only* your video card and its driver; other parameters could be:
```
sudo lshw -C multimedia
```
to list your sound card, and:
```
sudo lshw -C network
```
to list your network devices (ethernet and/or wireless card). You used **sudo** with lshw because the command itself suggests you use it with administrator privileges:

* sudo = **S**uper **U**ser **DO**

When Ubuntu is installed on your system, you'll have created an account with a corresponding password; this account is the administrator of the system, and to use administrative functions (such as installing programs or using administrative tasks from the "System->Administration" menu) you'll be prompted to enter your password.

Most of the time you won't need to use the terminal, but people might ask you to run certain commands to try and diagnose the issues you might be having.

Have fun, and please post back if you have problems with your setup.

Welcome to the community!

---

