---
title: "No Linux will boot up (LiveUSB)"
date: 2013-02-23
forum: Any Other OS
---

### Post by Andriel on 2013-02-23
Hallo,
I'm new to Linux and want to try it out, so I chose Linux Mint. I hope you can help me. :)
Now, I tried alot of things, I have a sheet full of commands, errors and boot parameters on my desk, but I can't get Linux to boot. This is my hardware configuration:

[LIST]
[*]ASRock B-75 Pro3-M - UEFI firmware
[*]Intel i5-3450
[*]Nvidia GeForce GTX 560Ti
[*]8GB Corsair RAM
[/LIST]
**Goal:** Dualboot Win7 64bit + Linux Mint 14 64bit
What I already tried:

[LIST]
[*]Various boot parameters: nomodeset, no(l)apic, acpi=off, reboot=bios, irqpoll
[*]Booting from different USB drives
[*]mint4win.exe
[/LIST]
How far I got:

[LIST=1]
[*]I have a Linux Mint 14 64bit USB created with Universal USB Installer.
[*]I boot it in UEFI mode. (if I try in BIOS mode it's the same problem)
[*]I edit the boot parameters for the first option - "Start Linux Mint":
[LIST=1]
[*]nouveau.modeset=0
[*]noquiet, nosplash
[/LIST]
 
[*]I get some rolling text ending with: "**[sdb] Attached SCSI removable disk**", below there is a blinking cursor, I can write something in this stage. If I press CTRL-ALT-DEL now, I can abort and restart UEFI.
[*]If I wait now, there comes more text, I think it's pretty much the same as in [COLOR=Blue][this post]("http://ubuntuforums.org/showthread.php?t=1982399&highlight=live+usb+boot+freeze")[/COLOR], this guy seems to have a similar problem with an ASRock motherboard. quote: > usb2-1-8: new full-speed USB device number 6 using ehci_hcd
ata7.00 exception Emask 0x52 SAct 0x0 SErr 0xffffffff action 0xe
 frozen
ata7: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt  CommWake 10B8B Dispar BadCRC HandShk LinkSeq TrStaTrns UnrecFIS DevExch }
ata7.00: failed command: IDENTIFY PACKET DEVICE
ata7.00: cmd a1/00:01:00:00:00:00/00:00:00:00:00:00/00 tag 0 pio 512 in
res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x56 (ATA bus error)
ata7.00: status: { DRDY }
ata7.00: hard resetting link After that, it freezes and I have to hard reboot. This happens, by the way, when choosing any of the options in the grub menu, including "Check Integrity of the Medium". The guy in the post linked above said he solved his problem by disconnecting his cd player, but how to do this, does he mean the cd/dvd drive and can I do it without opening my case?
[/LIST]
Any help is greatly appreciated! :)

---

### Post by sanderj on 2013-02-23
Annoying.

I would try this: Ubuntu 12.10 32-bit. Reasons:

- you will get more help here when you have Ubuntu questions
- there are problems reports of UEFI with 64-bit, which do not happen with 32-bit

HTH

---

### Post by Andriel on 2013-02-24
Sorry for the late reply, I have been busy.
But I found an UEFI option to disable all SATA connections. After that, every distro boots into the live session. :D

---

### Post by oldfred on 2013-02-24
The Ubuntu 32 bit version does not support UEFI boot only BIOS.

Does this motherboard have the asmedia ports like this one? They seem to be the one's causing issues.

       AsRock calls BIOS mode AHCI.

"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.

    
With nVidia you will also need nomodeset whether in BIOS or UEFI boot mode.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

