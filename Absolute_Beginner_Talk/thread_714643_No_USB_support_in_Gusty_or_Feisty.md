---
title: "No USB support in Gusty or Feisty"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by dteach on 2008-03-04
I've had trouble since day one with the USB support in Ubuntu.  I've tried updating kernel and various other solutions posted  but nothing seems to work.
here's what I got
Ubuntu 7.04 with 2.6.24-11
HP dv2225nr
Nvidia MCP51 chipset
broadcom 43xx wireless (fixed)

At this point $lsusb produces nothing at all

a little help would be greatly appreciated.  I really enjoy the idea of an open source OS, and don't want to ruin it because I can't use my USB ports.

---

### Post by talsemgeest on 2008-03-04
Shouldnt you upgrade to 7.10 ?

---

### Post by rebshalom on 2008-03-04
I have 7.10 installed and have the same problem. I cannot use any USB port.

---

### Post by sanddgroper on 2008-03-04
Hi
You could try booting off a live cd and see if they work off that.
I know it is a stupid question but you do have the usb ports connected
to the motherboard ie they have worked some time in the past.
Of course hardware problems are not new to computers.

Cheers
Sandy

---

### Post by dteach on 2008-03-04
I've read that Gusty and HPs aren't the best of friend, so I held off on the upgrade...until I got really frustrated last night and upgraded.  Same situation, and yes the USB ports have worked in the past.  and lsusb still does not return any results.

I will try the booting off the cd to see if that makes a difference.

---

### Post by dteach on 2008-03-04
booted off live CD,  no change.

---

### Post by sanddgroper on 2008-03-04
Hi
You could try looking in the following logs
dmesg
messages
syslog
For something like this

[   26.004455] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   26.004465] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 17
[   26.004481] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.004486] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   26.004868] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   26.004893] ohci_hcd 0000:00:02.0: irq 17, io mem 0xda004000
[   26.061631] usb usb1: configuration #1 chosen from 1 choice
[   26.061665] hub 1-0:1.0: USB hub found
[   26.061676] hub 1-0:1.0: 3 ports detected.
Now I dont know what ohci is but maybe you have to have it on your motherboard.

Cheers
Sandy

---

### Post by dteach on 2008-03-05
so this is what I came up with using dmesg

[   22.229953] usbcore: registered new interface driver usbfs
[   22.229976] usbcore: registered new interface driver hub
[   22.229993] usbcore: registered new device driver usb
[   22.230614] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.231002] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   22.231013] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 16
[   22.231025] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.231028] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   22.231172] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   22.231193] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xb0004000
[   22.266286] SCSI subsystem initialized
[   22.270890] libata version 2.21 loaded.
[   22.297617] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   22.318773] usb usb1: configuration #1 chosen from 1 choice
[   22.318799] hub 1-0:1.0: USB hub found
[   22.318811] hub 1-0:1.0: 8 ports detected
[   22.421065] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   22.421077] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 17
[   22.421088] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   22.421092] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   22.421116] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   22.421146] ehci_hcd 0000:00:0b.1: debug port 1
[   22.421150] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   22.421161] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xb0005000
[   22.421171] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.421242] usb usb2: configuration #1 chosen from 1 choice
[   22.421265] hub 2-0:1.0: USB hub found
[   22.421271] hub 2-0:1.0: 8 ports detected
[   22.529215] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.529221] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx


I wasn't sure what all was relevant... 
I the bright side my system is at least recognizing some sort of USB devices when I use lsusb


root@teach-laptop:~# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 0

---

### Post by sanddgroper on 2008-03-05
Hi
Well there does not seem to be any errors there.
Here is what I get in /var/log/messages when I plug a usb memory stick in.
[ 4114.991397] usb 3-5: new high speed USB device using ehci_hcd and address 3
 [ 4115.126376] usb 3-5: configuration #1 chosen from 1 choice
 [ 4115.234109] usbcore: registered new interface driver libusual
  [ 4115.257877] Initializing USB Mass Storage driver...
  [ 4115.262433] scsi2 : SCSI emulation for USB Mass Storage devices
  [ 4115.263877] usbcore: registered new interface driver usb-storage
  [ 4115.263888] USB Mass Storage support registered.
  [ 4120.256250] scsi 2:0:0:0: Direct-Access     USB      DISK Pro         1100 PQ: 0 ANSI: 0 CCS
  [ 4120.271703] sd 2:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
  [ 4120.272748] sd 2:0:0:0: [sdb] Write Protect is off
  [ 4120.275319] sd 2:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
  [ 4120.276066] sd 2:0:0:0: [sdb] Write Protect is off
  [ 4120.276081]  sdb: sdb1
You might like to check what you get when you plug in a usb device

Cheers
Sandy

---

### Post by Keltenbleich on 2008-03-05
Fascinating..! And what is the meaning of all that? Please, explain for beginners...

---

### Post by sanddgroper on 2008-03-05
Hi
Well in my last post it is just saying that a usb device has been connected.
In order to try and solve dteach's problem would like to know what happens
when he plugs in a usb device.
If a system is having a problem it may show up in the following files in /var/log
dmesg
messages
syslog

Cheers
Sandy

---

### Post by dteach on 2008-03-06
So there is no change at all in my message log when I plug in a USB device.  Could this be because I have Ehci and Ohci both installed...

---

### Post by dteach on 2008-03-06
Bump...  Does anyone have an answer for this.  It's the only piece of my system that doesn't work.

---

### Post by sanddgroper on 2008-03-06
Hi
> So there is no change at all in my message log when I plug in a USB device. Could this be because I have Ehci and Ohci both installed...
No to have Ehci and Ohci would seem to be normal.
My knowledge of USB is almost nil but the fact it is not showing in messages I guess says something.
Have you checked in /var/log in
dmesg and syslog when you plug the usb device in to see if they say anything.
Stupid question I know but you have tried more than one usb device.?
Cheers
Sandy

---

### Post by dteach on 2008-03-07
I checked a couple of times in both logs, with plugging in my ipod and thumb drive and neither of the devices changed the logs.  
something to note is that I do have power on both devices, ie. the light on my thumb drive lights up and my ipod charges while plugged in.

---

### Post by sanddgroper on 2008-03-07
Hi
I was playing around this morning and booted just into recovery mode.
When I got to the desktop I plugged in my usb device and it did not auto
mount and I got a warning about HAL(hardware abstraction layer not working).
Maybe you need to see if HAL is loaded for you on boot.
How you would do this I dont know sorry.

Cheers
Sandy

---

### Post by thisiam on 2008-03-07
My BIOS give me the option to enable and disable the USB ports. 
i would disable and save save settings and re enable them.
worth a shot. don't know if it will work as my USB ports all work fine out of the box.

---

### Post by sanddgroper on 2008-03-07
Hi Dteach
You might like to have a look at this site.
[http://www.linux-usb.org](http://www.linux-usb.org)

Cheers
Sandy

---

### Post by dteach on 2008-03-07
So I checked out that thread, and it didn't seem to offer anything as to a solution.  I've also looked into the Hardware Abstraction Layer and didn't seem to find any problems there either.
Once again my system can see the devices it just fails to recognize what they are.

```
 teach@teach-laptop:/$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```


it's driving me crazy

---

### Post by dteach on 2008-03-07
> **thisiam said:**
> My BIOS give me the option to enable and disable the USB ports. 
i would disable and save save settings and re enable them.
worth a shot. don't know if it will work as my USB ports all work fine out of the box.

I've also looked at the BIOS and I do not have the option to enable or disable USB ports in my BIOS.  It's an HP the BIOS is not very verbose.  I thought about updating the BIOS but I could not find a good way to do that with the current flash application given by HP.

Side Note: does anyone have a good solution to the BOIS upgrade.
here is the file I'm working with
[HP WinFlash]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-56219-1&lc=en&cc=us&dlc=en&product=3340127&os=228&lang=en")

---

### Post by dteach on 2008-03-09
Bump.... Still looking for an answer to this question.

---

### Post by dteach on 2008-03-10
Bump..

---

### Post by rklauco on 2008-04-25
Well, as I can see, I am not alone.
I have the same chipset, but different board vendor - Foxconn 6150 DVI.
I can see the exact same thing in my dmesg and in logs.
Eve though I found, that pluging in a device in the lower front USB plug creates third USB device in lsusb. This is the only USB plug working.
No other does, no matter if on the mainboard, or on the back of the machine - no response in dmesg after plugging any periferial.
The USB ports are working - I can plug in an formated USB stick with SLAX and boot.
My USB mouse is shining until kernel is loaded - in the moment of running ubuntu kernel, the mouse light goes off and I am out of USB :-(
I did a lot of googling, already tried acpi, noapic and lots of boot parameters with absolutely no effect.
Right now I am installing old XP to see, if the XP works...

---

