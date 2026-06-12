---
title: "Vexing Printer Issue"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by Goober on 2005-10-12
Hi Guys,

I am having a problem with my printerm, and it is vexing me.  I have the HP PSC1410, which, according to the [UbuntuWiki](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters?highlight=%28printers%29) works in Breezy.

But, it doesn't for me.  It was autodetected in Hoary, but it is not in Breezy.
The UbuntuWiki says it should be, and I have the right driver installed, but it simply doesn't work for Breezy.  I might have to select the right USB port, and I am not sure which one that is.

Can anybody give me a hand here?  I know this printer should work in Breezy, its just . . . not . . .

---

### Post by mlomker on 2005-10-12
Remove and reinsert the USB cable and then issue this command:

```

dmesg | tail

```

That'll tell you what port it is being assigned.

---

### Post by ubuntumaneh on 2005-10-12
Try also in terminal: lsusb

---

### Post by Goober on 2005-10-12
Ok, here are the results:

```

nathan13@nathan13:~$ dmesg | tail
[4294725.617000] apm: overridden by ACPI.
[4294728.341000] Bluetooth: Core ver 2.7
[4294728.341000] NET: Registered protocol family 31
[4294728.341000] Bluetooth: HCI device and connection manager initialized
[4294728.342000] Bluetooth: HCI socket layer initialized
[4294728.361000] Bluetooth: L2CAP ver 2.7
[4294728.361000] Bluetooth: L2CAP socket layer initialized
[4294728.394000] Bluetooth: RFCOMM ver 1.5
[4294728.394000] Bluetooth: RFCOMM socket layer initialized
[4294728.394000] Bluetooth: RFCOMM TTY layer initialized
nathan13@nathan13:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
nathan13@nathan13:~$

```

Umm . . . I'm not sure how to interpret this . . .

---

### Post by ubuntumaneh on 2005-10-12
I think your printer is not connected to the cpu. The reason may be many. But try yo disconnect and to connect in another usb port. Both methods should have worked. The second one has the advantage that you don't have to check behind your computer.

good luck

---

### Post by wylfing on 2005-10-12
I agree with that. Have you tried unplugging the USB cable, waiting 15 seconds, and plugging it back in?

---

### Post by Goober on 2005-10-12
[QUOTE=wylfing]I agree with that. Have you tried unplugging the USB cable, waiting 15 seconds, and plugging it back in?[/QUOTE]

No, but I'll unplug it, and then plug it into a different port.  The vexing thing about this is that port definitely works, since Hoary and Windoze recognize it.

I'll tell how it worked in a couple minutes.

---

### Post by Goober on 2005-10-12
Ok, some new data.  No, Breezy still doesn't recognize it.  This is a different port, and I waited about 30 seconds.

```

nathan13@nathan13:~$ dmesg | tail
[4294728.341000] Bluetooth: Core ver 2.7
[4294728.341000] NET: Registered protocol family 31
[4294728.341000] Bluetooth: HCI device and connection manager initialized
[4294728.342000] Bluetooth: HCI socket layer initialized
[4294728.361000] Bluetooth: L2CAP ver 2.7
[4294728.361000] Bluetooth: L2CAP socket layer initialized
[4294728.394000] Bluetooth: RFCOMM ver 1.5
[4294728.394000] Bluetooth: RFCOMM socket layer initialized
[4294728.394000] Bluetooth: RFCOMM TTY layer initialized
[4296351.973000] ibm_acpi: ec object not found
nathan13@nathan13:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
nathan13@nathan13:~$


```

---

### Post by wylfing on 2005-10-12
OK, some more questions and suggestions.

1. Did you dist-upgrade to Breezy?

2. Check Synaptic for hpijs and cousins. Are they all installed? Are any of them upgradeable?

3. Even if none of the hpijs/hpoj/etc. packages are upgradeable, try reinstalling them all. (In Synaptic, right-click the packages and choose Mark for reinstallation.) It would be best if the printer was unplugged during this process. Plug it back in after all the packages are upgraded/reinstalled.

---

### Post by Goober on 2005-10-12
1 - No, I installed a completely new install of Breezy on the same HD but a different partition.

2 - Will do so when I am back in Breezy.  I am currently in Hoary.

One more thing, since I am in Hoary (had do some printing), I typed those 2 things into the Command Terminal, and here is what I got (I think they will help)

```

nathan13@garagecomputer:~ $ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:4d11 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
nathan13@garagecomputer:~ $ dmesg | tail
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
eth0: no IPv6 routers present
usb 2-2: new full speed USB device using uhci_hcd and address 2
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4D11
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
nathan13@garagecomputer:~ $

```

By the way, thanks for all your help!  I'll be going back into Breezy shortly, so I can tell you how it worked very quickly.

---

### Post by mlomker on 2005-10-12
> Ok, some new data.  No, Breezy still doesn't recognize it.  This is a different port, and I waited about 30 seconds.


The printer is working fine in Windows on the same machine?  The printer drivers are not going to help you if the kernel isn't recognizing the printer at all.  Do you still have the Hoary kernel installed?  If so then try booting up on the 2.6.10 kernel (go into the grub menu) and see if it does anything different.

Either the kernel is bad or some other package didn't upgrade right...figuring out which one is the problem...

---

### Post by wylfing on 2005-10-12
My money is still on non-upgraded hpijs/hpoj or similar. I'm off to bed soon, but I'll check back in the morning :)

---

### Post by Goober on 2005-10-12
Ok, I'm back in Breezy with some excellent news.  I opened a terminal, typed in lsusb, and, like magic, it recognized the Printer on the same port as in Hoary.

Then, like magic, I went to the printing Wizard (or whatever it is called).  it recognized the printer, just like in Hoary.  So I printed a test page.  It worked!!!  Somehow, unplugging and then rebooting the computer convinced Breezy to recognize it.  

So, case closed, everything works, and this is a very happy Breezy user saying (ThankYouThankYouThankYou)^AstronomicallyHugePhysicallyImpossibleNumber.

---

### Post by mlomker on 2005-10-12
> My money is still on non-upgraded hpijs/hpoj or similar. I'm off to bed soon, but I'll check back in the morning

I'm thinking either HAL or DBUS is malfunctioning.  If you can't see the printer at the hardware level (lsusb) then the drivers won't matter...it's like worrying about ice cream flavors when the cone is missing.  :D

---

### Post by Goober on 2005-10-12
For the record, Synpatic shows hpijs as being installed, but not hpoj.  I am fairly sure that the Fundamental Problem was something to do with the usb connection not being recognized, as mlomker.  I know from others that this model printer works, its just that the USB connection didn't want to be recognized for some reason.

---

### Post by wylfing on 2005-10-13
Yep, you were right mlomker. Glad to see everything worked out.

Since I bet my money on it, here's my 50 cents. *Plink* :)

---

