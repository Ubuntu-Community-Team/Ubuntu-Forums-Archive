---
title: "ATI issues on Compaq nc6400 &amp; blank Xorg"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2008-02-01
Ubuntu is working well on my Compaq nc6400, except:

I installed Compiz manager but each time I turned it on via the manager nothing would happen (I do have the restricted drivers activated), I started it in terminal and it said:

> anthony@anthony-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

Doing some searches I found this thread:

[http://ubuntuforums.org/showthread.php?t=596938&highlight=nc6400](http://ubuntuforums.org/showthread.php?t=596938&highlight=nc6400)

I went ahead and did "sudo apt-get install xserver-xgl" in terminal which does kind of get things running but everything is very slow and its really hard to open GL Desktop, I just get a timer? on the second attempt it opens.

Also if I turn it off, next re-boot its back on again.

If I now open Compiz in terminal I now get:

> anthony@anthony-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I'm really a bit lost now and was going to give up on a bad job but cant as I cant even turn of Compiz as its back on after a re-boot (I guess I could remove it).

Any advice would be really appreciated.

---

### Post by jan quark on 2008-02-01
first of all pls post the result of the terminal command

```
lspci
```

then when we have made sure what video card you have we will see further

---

### Post by kudos1uk on 2008-02-01
> **jan quark said:**
> first of all pls post the result of the terminal command

```
lspci
```

then when we have made sure what video card you have we will see further

Thanks for taking a look at this for me, here is the result:

> anthony@anthony-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
anthony@anthony-laptop:~$ 


---

### Post by kudos1uk on 2008-02-01
error

---

