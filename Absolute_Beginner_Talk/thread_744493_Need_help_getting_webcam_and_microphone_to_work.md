---
title: "Need help getting webcam and microphone to work"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Stabilityonitsown on 2008-04-03
Hi guys before we start I just want to say I am using Debian.
Anyway to start it off, I just recently installed debian and tried to use my microphone(i have a headset btw) and it don't work, so I tried to use my webcam and it said webcam not found, so I searched around for a couple of hours, after that I found Gspca/Spca5xx and installed it and so far it still has not worked. And also here is the info
#lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp.
Bus 001 Device 004: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 001: ID 0000:0000

Help would be appreciated!:popcorn:!

---

### Post by Stabilityonitsown on 2008-04-03
Bump(Was on 3rd page)! Someone please help me ill thank you in return:(...

---

### Post by privaterolf on 2008-04-03
You've probably already tried this...but...

Have you gone to the volume manager and first of all, enabled, then turned on the volume on the microphone?

I'm looking for a solution to the webcam now..

---

### Post by Stabilityonitsown on 2008-04-03
> **privaterolf said:**
> You've probably already tried this...but...

Have you gone to the volume manager and first of all, enabled, then turned on the volume on the microphone?

I'm looking for a solution to the webcam now..Enable? Nah I haven't tried that but I am doing it now, ill report on the outcome.

---

### Post by pseudo-random on 2008-04-03
Can you run the ```
dmesg
```
command to search for references to your USB device: 04fc:0561?

---

### Post by Stabilityonitsown on 2008-04-03
Ok so I tried the microphone thing and it worked, but when I go to stickam and try it it says its really low but people still say they can hear me. And also random I have no clue as to what you mean.

---

### Post by privaterolf on 2008-04-03
> **Stabilityonitsown said:**
> Ok so I tried the microphone thing and it worked, but when I go to stickam and try it it says its really low but people still say they can hear me. And also random I have no clue as to what you mean.

Applications>Accessories>Terminal

Copy/paste (use right click to paste) and hit enter.

---

### Post by Stabilityonitsown on 2008-04-03
> **privaterolf said:**
> Applications>Accessories>Terminal

Copy/paste (use right click to paste) and hit enter.
Lol I know that, but all that code does is show a bunch of random lines. How is that supposed to help me.
Edit: Ok I re-read your post I just copy and paste the terminal text into a text editor then searched for 04fc:0561 and nothing came up so ya.

---

### Post by privaterolf on 2008-04-03
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Have you tried this page?

---

### Post by pseudo-random on 2008-04-03
[QUOTE= Stabilityonitsown]Lol I know that, but all that code does is show** a bunch of random lines.** How is that supposed to help me.
Edit: Ok I re-read your post I just copy and paste the terminal text into a text editor then searched for 04fc:0561 and nothing came up so ya.[/QUOTE]
Those random lines contain ton's of useful information about what your computer's been up to.
Try searching again for 'webcam' or 'usb'.

---

### Post by privaterolf on 2008-04-03
> **pseudo-random said:**
> Those random lines contain ton's of useful information about what your computer's been up to.
Try searching again for 'webcam' or 'usb'.

I believe usb is 

```
lsusb
```

Correct?

---

### Post by Stabilityonitsown on 2008-04-03
I snipped out a peice that had a bunch of "usb" strings in it. Here it is.
```
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000ff80
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 177
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.1: irq 177, io base 0x0000ff60
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
e100: Copyright(c) 1999-2005 Intel Corporation
ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 169
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: UHCI Host Controller
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000ff20
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 185
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:1d.7: debug port 1
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: irq 185, io mem 0xffa80800
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 8 ports detected
usb 1-1: new low speed USB device using uhci_hcd and address 2
ICH5: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 193
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: ST380011A, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
usb 1-1: new low speed USB device using uhci_hcd and address 3
usb 1-1: configuration #1 chosen from 1 choice
usb 1-2: new full speed USB device using uhci_hcd and address 4
usb 1-2: configuration #1 chosen from 1 choice
hdc: HL-DT-ST DVD+/-RW GWA4164B, ATAPI CD/DVD-ROM drive
usb 2-1: new low speed USB device using uhci_hcd and address 2
ide1 at 0x170-0x177,0x376 on irq 15
usb 2-1: configuration #1 chosen from 1 choice
usbcore: registered new driver hiddev
ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 201
e100: eth0: e100_probe: addr 0xfeaef000, irq 201, MAC addr 00:16:76:0E:33:12
input: Dell Dell USB Mouse as /class/input/input0
input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.0-1
input: Dell Dell USB Keyboard as /class/input/input1
input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
```

---

