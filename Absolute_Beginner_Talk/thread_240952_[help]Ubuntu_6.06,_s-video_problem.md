---
title: "[help]Ubuntu 6.06, s-video problem"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by yusy on 2006-08-21
I installed Ubuntu 6.06 on my laptop (thinkpad T42 radeon 7500).
everything works good, but s-video doesn't.
I installed tpb.
when I pressed the "Fn+F7"
I can see " LCD on, CRT off" "LCD on, CRT on" .... on LCD, but no signal comes out of the s-video.

please help me 

thx

---

### Post by rowanparker on 2006-08-21
What video card does it use?

---

### Post by yusy on 2006-08-22
here is my lspci:
--------------------------------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
-------------------------------------------------------------------

---

### Post by gaelfx on 2006-08-23
I have had a similar problem. I restarted my computer a couple of times, and eventually the signal came through. It works fine whilst booting up, however, the signal seems to become disrupted once Ubuntu gets going. One thing I think that helps is to make sure the monitor is on before you start up your computer, as this seemed to be a problem as I started the computer. I will try some more tricks tonight and let you know what I find. Also, are you using two monitors at once, such as an LCD monitor and your TV? I'm just curious about your set up compared to mine.

---

### Post by yusy on 2006-08-24
> **gaelfx said:**
> I have had a similar problem. I restarted my computer a couple of times, and eventually the signal came through. It works fine whilst booting up, however, the signal seems to become disrupted once Ubuntu gets going. One thing I think that helps is to make sure the monitor is on before you start up your computer, as this seemed to be a problem as I started the computer. I will try some more tricks tonight and let you know what I find. Also, are you using two monitors at once, such as an LCD monitor and your TV? I'm just curious about your set up compared to mine.
ok, looking forward

---

### Post by kronepils on 2006-09-12
So, how did it go? Is TV-out working for you??
I can't get it to work on my T42.
I found this link to patch the driver, but it would be nice not having to...
[http://megahurts.dk/rune/tv_output.html]("http://megahurts.dk/rune/tv_output.html")


Looking forward to hear from you!

---

