---
title: "BIOS  Problem / Hard Drive Not Recognized ... Kinda"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by ryangoff on 2007-09-14
SOLVED! The problem was that it was trying to boot off the 3.5" disk first. I don't have a 3.5" disk installed, so that's why I didn't think to check. (it recognized the 3.5" because I installed a card reader in the slot for cameras.)

I just built my first computer ever. Go me. But, I'm having a little trouble before Ubuntu even starts up. As it's starting up, I get this:

```
IDE Channel 0 Master : None
IDE Channel 0 Slave  : None

IDE Channel 2 Master : LITE-ON DVDRW LH-20A1S 9L08
IDE Channel 3 Master : HDS728080PLA380

Floppy disk(s) fail (40)

Press F8 to Enable System Configuration
Press F9 to Select Booting Device after POST
Press F1 to continue, DEL to enter SETUP
03/26/2007-NF-MCP61-6A61KB02C-00
```

Never hurts to be thorough, right? Anyway, it hangs there, but if you hit F1 to continue, it goes merrily on its way to start the OS. The problem is just more of a nuisance than anything else, but I was wondering if anyone could help me so that after BIOS, it starts loading straight to Ubuntu.

 I'm using a SATA hard drive (Hitachi Deskstar) and the LITE-ON DVD (SATA Data and Power), which could be part of the problem since it's talking about IDE Master/Slave.

Oh .. and what is POST. I keep on hearing it, but haven't quite figured out exactly what it is yet.

---

### Post by wolfen69 on 2007-09-15
P.O.S.T (power on self test)

Abbreviated POST, a diagnostic testing sequence run by a computer&#8217;s BIOS as the computer&#8217;s power is initially turned on. The POST will determine if the computer&#8217;s RAM, disk drives, peripheral devices and other hardware components are properly working. If the diagnostic determines that everything is in working order, the computer will continue to boot. 

as far as your other problem, press del key at bootup, go to boot tab, and select the hard drive as first or second boot device. obviously if you make cd first, it will boot first if loaded.

---

### Post by ryangoff on 2007-09-15
Thanks .. I got it to work. Solution in the original post...

---

