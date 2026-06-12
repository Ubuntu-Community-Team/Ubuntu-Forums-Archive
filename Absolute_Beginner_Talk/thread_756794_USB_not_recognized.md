---
title: "USB not recognized?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by dover19 on 2008-04-16
I'm new at Linux and I just installed Xubuntu on an old P2 Toshiba Laptop (Tecra 8000). It has a USB port but ever since I installed Linux, I'm not sure if it works anymore.

I got a USB-2-LAN adapter because it has no network card and when I plugged it in it didn't see any new hardware or anything. I figured I should try jsut a regular flash drive, it should be able to see that, but nope, nothing.

So I'm kind of asking 2 things.

1-How do I install new hardware?

2-How do I see a list of the currently installed hardware and if it's working properly?

Thanks

---

### Post by philinux on 2008-04-16
In a terminal use

[FONT="Comic Sans MS"]ls pci

then 

ls usb[/FONT]

---

### Post by neurostu on 2008-04-16
What is the part / model number of your usb 2 lan device?

---

### Post by dover19 on 2008-04-16
I tried typing "ls pci" and "ls usb" in the terminal and they both say "No such file or directory".

Here's a link to where I bought the USB-LAN adapter from:
[http://factorydirect.ca/catalog/product_spec.php?pcode=US0130](http://factorydirect.ca/catalog/product_spec.php?pcode=US0130)

The box doesn't have any kind of model name or number really, it has only what seams like a product code from the store itself (US0130).

---

### Post by philinux on 2008-04-16
Sorry, hayfever got me.

No spaces


lsusb

lspci

---

### Post by dover19 on 2008-04-16
lspci:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
00:04.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
00:0b.0 CardBus Bridge: Toshiba America Info Systems ToPIC97 (rev 05)
00:0b.1 CardBus Bridge: Toshiba America Info Systems ToPIC97 (rev 05)

lsusb (with USB-LAN):

Bus 001 Device 002: ID 0a46:9601 Davicom Semiconductor, Inc.
Bus 001 Device 001: ID 0000:0000

lsusb (with USB Flash Device):

Bus 001 Device 001: ID 0000:0000

---

### Post by philinux on 2008-04-16
Ok so the system is seeing your davicom usb device.

Which version of xubuntu have you installed?

---

### Post by dover19 on 2008-04-16
The latest one...7.10.

So, is this how you check your hardware (lspci) there's no "device manager" window or anything like that?

If I understand this properly, according to the lsusb command it's not seeing my flash drive.

It's detecting the USB-LAN, but how do you know if it's recognized and actually working properly?

Sorry for all these questions, I'm just trying to learn this new OS and how things works lol.

---

### Post by philinux on 2008-04-16
Ok thats good as 7.1 should play nice with the davicom device.

For the usb flash drive. Well plug it in, see if the led lights up. Also in the terminal type

dmesg

and look at the last few lines see if there are any errors relating to the flash drive.

---

### Post by dover19 on 2008-04-16
I don't really see an error message regarding the USB Flash Drive specifically. The only error message I can see in the last couple of lines is: 
Failure registering capabilities with primary security module.

I just inserted a PCMCIA Lan Card (shut-down, rebooted) and when i checked lspci I can see that it recognizes it. So basically, am I right to assume that when a new piece of hardware is installed Ubuntu will not give you any type of notification? You have to check if it's showing up using lspci? That would mean that my USB-LAN probably works, I just have to setup my network settings properly (I'm not currently at home, I'm at the office and I need certain settings to get on the network, so it's not as simple as hooking it up and loading yahoo.com).

---

### Post by philinux on 2008-04-16
Yep mainly ubuntu has all the drivers it needs. It just works usually.

Things like digicams should show up when connected as should usb drives. Mine appears on the desktop.

---

### Post by dover19 on 2008-04-16
Ok, I guess that means my USB Fash Drive doesn't work with Linux because nothing is showing up on my desktop. I'll try and get a different Flash Drive and see if it will work.

---

