---
title: "Wireless issues - 3 weeks now"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Paradoxed on 2006-12-30
Acer/extensa... please help !!


[I]~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

steve@steve-laptop:~$ sudo -s
root@steve-laptop:~# ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
root@steve-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
root@steve-laptop:~# dmesg | grep acer
[17180034.440000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17180034.440000] acer_acpi: No WMI interface, unable to load.
[17180060.236000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17180060.236000] acer_acpi: No WMI interface, unable to load.
[/I]

---

### Post by boydjj on 2006-12-30
There is a brief guide at [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsPackardBell?highlight=A5560]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsPackardBell?highlight=A5560") about your card. Search the page there for "INPROCOMM IPN 2220" - it's a different laptop, but the fix should be the same.

You might also try searching the forums for the same phrase and see if anyone's posted a similar problem.

---

### Post by diepruis on 2006-12-30
This should really be placed under Network & Wireless under Main Support Categories. That said, what is the output of ...
```

lscpi -n

```
... and what have you done to solve the problem up to now?

---

### Post by Paradoxed on 2006-12-30
Thanks for that. Seems like I am making some headway....


sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now if only I could the acer hotkey working...

---

