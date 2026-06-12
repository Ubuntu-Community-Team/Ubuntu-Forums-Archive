---
title: "[SOLVED] Updating BIOS in Ubuntu"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-12-20
How can I update my BIOS in ubuntu?
It is an old computer running xubuntu an it says that my bios is old when I start the computer up, it would be nice to update the bios to a newer one but how do I do it?

---

### Post by stump138 on 2007-12-20
You'll need to get the updated bios from your motherboard/system manufacturer and it is generally carried out via an installation from floppy disk.

what motherboard do you have?

---

### Post by DarKnyht on 2007-12-20
If you could post the information about your computer (model, BIOS type, etc.) it would make knowing what to tell you easier.

---

### Post by spydon on 2007-12-20
It is a computer that i built for a few years ago. Here is the lspci:
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:0c.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
01:00.0 VGA compatible controller: Intel Corporation 82740 (i740) AGP Graphics Accelerator (rev 21)

```

I shall just reboot and check which bios it is.

---

### Post by spydon on 2007-12-20
Okay here is the BIOS info:

ROM PCI/ISA BIOS (2A69KF09)
CMOS SETUP UTILITY
AWARD SOFTWARE, INC.

---

### Post by philinux on 2007-12-20
If its a 440bx its the phoenix bios. Same as mine.

The error I got at start up was - bios pre 2000 acpi=force needed or similar.

There is a jan 2000 phoenix bios which I used.

---

### Post by stump138 on 2007-12-20
The model # of your board will be stamped with white ink as it appears to be an intel board, generally in between the PCI slots.

Downloads and instructions for intel motherboards can be found here:

[http://www.intel.com/support/motherboards/desktop/sb/CS-022312.htm]("http://www.intel.com/support/motherboards/desktop/sb/CS-022312.htm")

Unless your board was made by someone else, that would be the place to start.  General consensus is that you should never update your bios unless you have issues, that said I do it as needed.  You should exercise caution though:)

---

### Post by spydon on 2007-12-20
> **philinux said:**
> If its a 440bx its the phoenix bios. Same as mine.

The error I got at start up was - bios pre 2000 acpi=force needed or similar.

There is a jan 2000 phoenix bios which I used.

Yeah I got that one too.

---

### Post by spydon on 2007-12-20
> **stump138 said:**
> The model # of your board will be stamped with white ink as it appears to be an intel board, generally in between the PCI slots.

Downloads and instructions for intel motherboards can be found here:

[http://www.intel.com/support/motherboards/desktop/sb/CS-022312.htm]("http://www.intel.com/support/motherboards/desktop/sb/CS-022312.htm")

Unless your board was made by someone else, that would be the place to start.  General consensus is that you should never update your bios unless you have issues, that said I do it as needed.  You should exercise caution though:)

Thx. I don't mind if the computer crashes ;)

---

### Post by Inxsible on 2007-12-20
I too wanted to update the BIOS on two of my old machines. I got the BIOS from the manufacturer's website (Toshiba)

You have to look for your old model if the model has been discontinued. Try and see if the manufacturer has downloads available. That way, you'd be sure the BIOS would work on your machine.

Trouble is, I don't have a floppy drive in the damn machine. So I am not sure how to update the thing :(
 Funny thing is they have an exe with which to update the BIOS from withing Windows, but I don't have windows on those machines

---

### Post by philinux on 2007-12-20
If its the SE440BX-2. then this is the update which I used.

[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=208&DwnldID=3519&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=208&DwnldID=3519&lang=eng)

---

