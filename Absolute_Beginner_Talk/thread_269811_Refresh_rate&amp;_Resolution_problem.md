---
title: "Refresh rate&amp; Resolution problem"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by umairsaeed219 on 2006-10-02
I have philiphs 15 inch monitor
Model no 105S7S42
How can i adjust the resolution and espically the refresh rate.

---

### Post by bulldog on 2006-10-02
In most cases it helps if you install your graphics card driver.

---

### Post by petri on 2006-10-02
If you don't know what your graphics is write **lspci** in terminal and post it here.

If you have drivers installed paste this in terminal
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions. If you don't know the answer leave the default alternative and just press Enter.

When you get to the resolution part you can mark with pressing your Spacebar. 
Afterwards restart your X with **Ctrl** + **Alt** + **Backspace** and wait till you get the graphical login.

Didn't help? Ask more.

---

### Post by umairsaeed219 on 2006-10-02
I ha posted the reult of lspci
idonot know whether or not driver is installed or not because i thought ubuntu might automaticallly pick up it
umair@umair-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Co ntroller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G] /GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interfa ce Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev  01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:02.0 Communication controller: Intel Corporation 536EP Data Fax Modem

---

### Post by petri on 2006-10-02
But you have done the sudo dpkg-reconfigure xserver-xorg ?



EDIT: ...and ofcourse you have tried  System > Preferences > Screen resolution?

---

### Post by umairsaeed219 on 2006-10-03
Hi petri
i have acted according to  your sugggestion and 
sudo dpkg-reconfigure xserver-xorg has worked for me
thanks a lot

---

### Post by petri on 2006-10-03
That's great! And it's great that you tell that to us so the next one with similar problem may find a solution quicker.

---

