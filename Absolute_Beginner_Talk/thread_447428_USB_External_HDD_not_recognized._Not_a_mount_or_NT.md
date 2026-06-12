---
title: "USB External HDD not recognized. Not a mount or NTFS problem."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by giallofever on 2007-05-18
I have scoured ubuntuforums and Google and no luck. I have an usb external HDD formatted in NTFS. It works in windows. It automounts on a fresh install of Edgy (my dad's PC.) Take it to my room with fresh Feisty install, it won't even recognize the drive. I have it turned on right now and here are some results. Let me know if you need any other reports.

Here is $ mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /home type ext3 (rw,errors=remount-ro)

Here is $ lsusb:

Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000  

Any ideas why it won't recognize?
Thanks

---

### Post by trent dillman on 2007-05-18
...

---

### Post by giallofever on 2007-05-18
> **trent dillman said:**
> does ```
sudo fdisk -l /dev/sda
``` say anything?

Nope.

---

### Post by giallofever on 2007-05-18
Here is the whole fdisk -l:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

---

### Post by trent dillman on 2007-05-18
...

---

### Post by giallofever on 2007-05-18
> **trent dillman said:**
> search /var/log/ for more details, and switch usb ports. maybe mount as a network share on dad's pc? (yeah, open his box up to even more nastiness...bad idea :-P)

I checked /var/log and really didn't know what file to look for but I found opened the 'udev' file and didn't see anything about 'sda', just my other drives, hda and hdb. I would like to have it connected in my room, but I am going to upgrade him to Feisty soon and would like to resolve this before I do so I have access to the drive somewhere in the house.

---

### Post by dfreer on 2007-05-18
post output of dmesg?

EDIT: actually just post dmesg | tail, there's a lot of info in there that isn't needed. just the last few lines that mention the usb device being plugged in

---

### Post by giallofever on 2007-05-18
Here is what dmesg | tail gave me:

[19622.915159] end_request: I/O error, dev hdc, sector 4344988
[19622.916448] hdc: tray open
[19622.916778] end_request: I/O error, dev hdc, sector 4344992
[19622.917243] hdc: tray open
[19622.917571] end_request: I/O error, dev hdc, sector 4344996
[19622.918070] hdc: tray open
[19622.918397] end_request: I/O error, dev hdc, sector 4344992
[19622.918863] hdc: tray open
[19622.919188] end_request: I/O error, dev hdc, sector 4344996
[19622.919675] hdc: tray open

No usb stuff mentioned so I searched through it and found all the usb stuff, if you need more let me know.

[   22.124922] usbcore: registered new interface driver usbfs
[   22.124942] usbcore: registered new interface driver hub
[   22.124965] usbcore: registered new device driver usb
[   22.125562] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.125919] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   22.125927] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   22.125939] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.125942] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   22.126076] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   22.126092] ohci_hcd 0000:00:02.0: irq 16, io mem 0xed085000
[   22.149107] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   22.181393] SCSI subsystem initialized
[   22.185806] libata version 2.20 loaded.
[   22.203183] usb usb1: configuration #1 chosen from 1 choice
[   22.203217] hub 1-0:1.0: USB hub found
[   22.203228] hub 1-0:1.0: 3 ports detected
[   22.304566] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   22.304575] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   22.304589] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   22.304592] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   22.304611] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   22.304628] ohci_hcd 0000:00:02.1: irq 17, io mem 0xed082000
[   22.353643] Floppy drive(s): fd0 is 1.44M
[   22.362159] usb usb2: configuration #1 chosen from 1 choice
[   22.362189] hub 2-0:1.0: USB hub found
[   22.362200] hub 2-0:1.0: 3 ports detected
[   22.378395] FDC 0 is a post-1991 82077
[   22.464484] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   22.464493] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   22.464504] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   22.464507] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   22.464536] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   22.464569] ehci_hcd 0000:00:02.2: debug port 1
[   22.464573] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   22.464583] ehci_hcd 0000:00:02.2: irq 18, io mem 0xed083000
[   22.464590] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.464645] usb usb3: configuration #1 chosen from 1 choice
[   22.464667] hub 3-0:1.0: USB hub found
[   22.464674] hub 3-0:1.0: 6 ports detected
[   22.568406] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   22.568411] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   22.568418] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   23.031559] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   23.088071] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[   23.090672] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   23.090694] NFORCE2: chipset revision 162
[   23.090696] NFORCE2: not 100% native mode: will probe irqs later
[   23.090701] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   23.090703] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   23.090708] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   23.090717]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   23.090728]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   23.090736] Probing IDE interface ide0...
[   23.164205] usb 3-1: configuration #1 chosen from 1 choice
[   23.164281] hub 3-1:1.0: USB hub found
[   23.164386] hub 3-1:1.0: 4 ports detected
[   23.379411] hda: WDC WD1200JB-00GVA0, ATA DISK drive
[   23.659199] hdb: WDC WD1200JB-00GVA0, ATA DISK drive
[   23.720017] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.750043] Probing IDE interface ide1...
[   23.758986] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   23.984357] usb 1-2: configuration #1 chosen from 1 choice
[   23.997485] usbcore: registered new interface driver hiddev
[   24.006492] input: Microsoft Microsoft IntelliMouse® Optical as /class/input/input2
[   24.006595] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Optical] on usb-0000:00:02.0-2
[   24.006609] usbcore: registered new interface driver usbhid
[   24.006612] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

---

### Post by dfreer on 2007-05-18
hmm and that is with the USB hard drive plugged in (should unplug it and replug it into a different slot, and then try dmesg. I don't see any messages about it being plugged in, much less any errors other than I/O error on hdc, and since USB drives are listed as sdx I don't think that is the problem.

---

### Post by kelvin spratt on 2007-05-18
giallofever you need to tell folks more about your computer and the os your using in your bedroom  for people to help you

---

### Post by giallofever on 2007-05-18
> **dfreer said:**
> hmm and that is with the USB hard drive plugged in (should unplug it and replug it into a different slot, and then try dmesg. I don't see any messages about it being plugged in, much less any errors other than I/O error on hdc, and since USB drives are listed as sdx I don't think that is the problem.

To make sure it was still good a drive, I just plugged into Edgy. It auto mounted.

I have 4 onboard usb ports on my PC (in sets of 2). I have tried it on all of them. I plugged it into another port (on the other set of 2 just in case I was having problems with one hub), and here is the dmesg results:

[   22.124922] usbcore: registered new interface driver usbfs
[   22.124942] usbcore: registered new interface driver hub
[   22.124965] usbcore: registered new device driver usb
[   22.125562] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.125919] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   22.125927] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   22.125939] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.125942] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   22.126076] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   22.126092] ohci_hcd 0000:00:02.0: irq 16, io mem 0xed085000
[   22.149107] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   22.181393] SCSI subsystem initialized
[   22.185806] libata version 2.20 loaded.
[   22.203183] usb usb1: configuration #1 chosen from 1 choice
[   22.203217] hub 1-0:1.0: USB hub found
[   22.203228] hub 1-0:1.0: 3 ports detected
[   22.304566] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   22.304575] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   22.304589] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   22.304592] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   22.304611] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   22.304628] ohci_hcd 0000:00:02.1: irq 17, io mem 0xed082000
[   22.353643] Floppy drive(s): fd0 is 1.44M
[   22.362159] usb usb2: configuration #1 chosen from 1 choice
[   22.362189] hub 2-0:1.0: USB hub found
[   22.362200] hub 2-0:1.0: 3 ports detected
[   22.378395] FDC 0 is a post-1991 82077
[   22.464484] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   22.464493] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   22.464504] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   22.464507] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   22.464536] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   22.464569] ehci_hcd 0000:00:02.2: debug port 1
[   22.464573] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   22.464583] ehci_hcd 0000:00:02.2: irq 18, io mem 0xed083000
[   22.464590] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.464645] usb usb3: configuration #1 chosen from 1 choice
[   22.464667] hub 3-0:1.0: USB hub found
[   22.464674] hub 3-0:1.0: 6 ports detected
[   22.568406] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   22.568411] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   22.568418] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   23.031559] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   23.088071] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[   23.090672] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   23.090694] NFORCE2: chipset revision 162
[   23.090696] NFORCE2: not 100% native mode: will probe irqs later
[   23.090701] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   23.090703] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   23.090708] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   23.090717]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   23.090728]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   23.090736] Probing IDE interface ide0...
[   23.164205] usb 3-1: configuration #1 chosen from 1 choice
[   23.164281] hub 3-1:1.0: USB hub found
[   23.164386] hub 3-1:1.0: 4 ports detected
[   23.379411] hda: WDC WD1200JB-00GVA0, ATA DISK drive
[   23.659199] hdb: WDC WD1200JB-00GVA0, ATA DISK drive
[   23.720017] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.750043] Probing IDE interface ide1...
[   23.758986] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   23.984357] usb 1-2: configuration #1 chosen from 1 choice
[   23.997485] usbcore: registered new interface driver hiddev
[   24.006492] input: Microsoft Microsoft IntelliMouse® Optical as /class/input/input2
[   24.006595] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Optical] on usb-0000:00:02.0-2
[   24.006609] usbcore: registered new interface driver usbhid
[   24.006612] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

---

### Post by giallofever on 2007-05-18
A7N8X-E Deluxe motherboard with an AMD3200.
2x 512MB DDR400
ATI Radeon 9550
D-Link WDA-2320 Wireless NIC
2x WD1200 120GB
and some DVDRW I threw in temporarily.

This occurred when I first installed Feisty. If this adds anything... my System>Hardware Information won't open, it briefly pops up then closes. All other menu items seem to work. My /home folder is on one hard drive by itself, but this problem was occurring before I moved it. I installed pmount and usbmount because I thought that might help. And besides a few Add/Remove and Automatix, I haven't touched this install really.

EDIT: This is stressful, I'm going to get cigarettes, BRB. :)

---

### Post by giallofever on 2007-05-19
OK, so I downgraded from Feisty to Edgy. I turn on my external usb hard drive (NTFS) and it shows up under Place>Computer as EXTERNAL with its little USB icon :). So when I try to open it or mount it I get:

$logfile indicates unclean shutdown (0, 0)
failed to mount '/dev/sda1': operation not supported
mount is denied because ntfs logfile is unclean. choose one action:
boot windows and shutdown it cleanly, or if you have a removable
device then click the 'safely remove hardware' icon in the windows
taskbar notification area before disconnecting it.
or
run 'ntfsfix' on linux unless you have vista, then mount ntfs with
the 'force' option read-write, or with the 'ro' option read-only.
or
mount the ntfs volume with the 'ro' option in read-only mode.
error: could not execute pmount

I have the Automatix read/write NTFS and FAT32 installed.

I was going to attempt to fix this by trying ntfsfix, but I thought I might get some input from somebody more knowledgeable in case there was another way or easier way. I feel like I have done enough damage to it as it is when turning it off/on without choosing unmount. I did this awhile back when I first installed Ubuntu, I was new to this.

Here is $fdisk -l :

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

And here is $mount :

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

NOTE: I also have an internal drive formatted EXT3 that refuses to automount as I have tried to make it my /home folder. Always getting fsck error on boot. But that's another issue. One at a time guys, right! :)

---

### Post by giallofever on 2007-05-20
Just upgraded to Feisty again, and it won't recognize it. Any new ideas on this? I have been trying to solve this forever because I want to stay on Feisty. It always auto mounts on Edgy but won't even show up on $lsusb, $mount, $fdisk in Feisty. My $lsusb, $fdisk, & $mount have already been included in this thread if you need them. Any Ubuntu wizards out there feel like taking on a mystery?

WOW! I hadn't thought of it before, but I plugged it into my LCD monitor USB port and it auto mounts. Any reason for this? I know I should just accept it, but I am determined as to why the PC's USB ports will not recognize it. To solve the problem per say.

Wait! It just unmounted itself. It seems I am back to square one.

---

### Post by Chemist on 2007-05-21
hi guys i've been having trouble ejecting my external usb devices so I ran the follwoing command. sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

i can now unmount my external USB devices however the mouse buttons on my laptop have stopped working. I've tried renaming the bak file to the orginal name and rebooting but with no luck. can someone please help

---

### Post by Mr.Beast on 2007-05-21
I've Just had a quick read though this, I'm not sure if you mentioned it before, but is the disk USB powered or does it have a power supply. Also I'm wondering if the monitor ports are acting as a powered USB hub and perhaps this may be related to a power issue on the USB bus ?  Just a thought.

---

### Post by giallofever on 2007-05-21
The USB HDD has an external power source. The monitor has two USB ports on the side, power is not an issue with them of course. But on the back of my mainboard, I have two sets of 2 USB ports. I have tried them all and none of them work. I have two USB ports on the front of the PC case that I haven't tried because I haven't hooked them up yet. But both my Dad and I both had fresh installs of Feisty, it auto mounts on his and isn't even recognized on mine. Hooking it up on the back or the front of his case works. When I install Edgy 6.10, it auto mounts perfectly. When I upgrade, it's gone. Feisty is being quite Feisty! :)

---

### Post by dfreer on 2007-05-21
well, I'm guessing if it works on your dad's fresh feisty install, but not yours, it is probably an hardware issue.

---

### Post by giallofever on 2007-05-21
> **dfreer said:**
> well, I'm guessing if it works on your dad's fresh feisty install, but not yours, it is probably an hardware issue.

We have the same motherboard. Other than me having a faster CPU & graphics card.

It's odd, It briefly mounts when plugged into my monitor but that's it.

I will prevail eventually! I am going to make Linux my bitch when I am done with this :)
*excuse the language*

---

### Post by dfreer on 2007-05-22
is there any other USB device that works, like mice, flash drives? because your monitor plugs into your main MoBo USB anyways, so if there is a problem with the onboard USB ports it'll affect your monitor's USB as well. but really I'm just guessing here, it doesn't make sense that it'll work on one Feisty PC and not the other, especially after multiple reinstalls.

EDIT: btw, great attitude to have, most people come across problems like this and just give up instead of trying to work the problem out.

---

### Post by smileysmoke on 2007-05-23
i had this same issue in feisty after upgrading from edgy.
my front usb ports dont want to work but my monitor usb worked :| strange
the only thing i have done is reinstall ntfs-3g, rebooted then plugged into the other usb port.

if you want any outputs etc let me know mate

---

