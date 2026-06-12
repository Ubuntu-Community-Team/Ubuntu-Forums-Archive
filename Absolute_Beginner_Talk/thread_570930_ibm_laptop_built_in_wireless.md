---
title: "ibm laptop built in wireless"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by tronnix75 on 2007-10-08
i have a IBM t40p thinkpad laptop, with built in wireless, how or what do i do to get linux to see the wireless chipset..

---

### Post by overdrank on 2007-10-08
> **tronnix75 said:**
> i have a IBM t40p thinkpad laptop, with built in wireless, how or what do i do to get linux to see the wireless chipset..

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by tronnix75 on 2007-10-08
ok will do

---

### Post by tronnix75 on 2007-10-08
here is the output of that command:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)



i guess i would also need to update my video drivers as well, i need the app that goes with the ati to be able to switch between monitors like the laptop monitor and a tv:)

---

### Post by tronnix75 on 2007-10-08
can anyone respond to this??:(

---

### Post by overdrank on 2007-10-08
> **tronnix75 said:**
> can anyone respond to this??:(

Be patient, Here is a thread that may help
[http://ubuntuforums.org/showthread.php?t=545779&highlight=Atheros+Communications%2C+Inc.+AR5211](http://ubuntuforums.org/showthread.php?t=545779&highlight=Atheros+Communications%2C+Inc.+AR5211)
As for you ati drivers have you enabled the restricted drivers located under system, administration.

---

