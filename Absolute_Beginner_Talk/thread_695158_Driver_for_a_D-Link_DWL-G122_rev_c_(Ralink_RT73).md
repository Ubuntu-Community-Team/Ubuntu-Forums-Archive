---
title: "Driver for a D-Link DWL-G122 rev c (Ralink RT73)"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Dissident85 on 2008-02-12
Hi all, I am trying to install the drivers for a wirless card that I have. It’s a Driver for a D-Link DWL-G122 rev c (Ralink RT73)… on my laptop I have a built in wireless card which I use for my every day internet use… but I want to use my external Link DWL-G122 for other programs. Can someone advise me on how to install the drivers for a Ralink RT73 chip set. 

And im not sure if anyone here can help me anyone know how to get aircrack to use the D-Link DWL-G122 not the internal network card?

---

### Post by mrsteveman1 on 2008-02-12
The driver for the RT73 should be included if its part of the current kernel (I'm not sure if it is or not), if not the only option is to download the source for a driver and compile it. You may have problems installing an external driver because things have changed so much in the wireless drivers recently.

The driver ralink wrote is [here]("http://www.ralinktech.com.tw/data/drivers/2008_0117_RT73_Linux_STA_Drv1.1.0.0.tar.bz2")

The serialmonkey driver may not compile correctly, but it is [here]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz")

If you need help compiling it and installing it post back.

Aircrack really just cracks preexisting files, if you mean airodump you should be able to just specify an interface when you use the program.

---

### Post by Dissident85 on 2008-02-12
> **mrsteveman1 said:**
> 
Aircrack really just cracks preexisting files, if you mean airodump you should be able to just specify an interface when you use the program.

so use something like

```
ipconfig
```

---

### Post by mrsteveman1 on 2008-02-12
Well, when you run airodump you specify an interface to capture from. Note that the interface has to support monitor mode in the first place for this to work, and if the interface does support monitor mode you must put it INTO monitor mode first before using it for capturing packets.
[URL="http://www.aircrack-ng.org/doku.php?id=airodump-ng&DokuWiki=40f3119273941be25f16704bc1f6c119"]
link
[/URL]

---

### Post by Dissident85 on 2008-02-12
> **mrsteveman1 said:**
> Well, when you run airodump you specify an interface to capture from. Note that the interface has to support monitor mode in the first place for this to work, and if the interface does support monitor mode you must put it INTO monitor mode first before using it for capturing packets.
[URL="http://www.aircrack-ng.org/doku.php?id=airodump-ng&DokuWiki=40f3119273941be25f16704bc1f6c119"]
link
[/URL]

thanks,

I just found a good tutorial.
[WEP Auditing with VMplayer, BackTrack, Aircrack and the DLink DWL-G122 USB Adapter]("http://www.irongeek.com/i.php?page=videos/glj12-wep-cracking-with-vmplayer-backtrack-aircrack-and-dlink-dwl-g122-usb")

---

### Post by mrsteveman1 on 2008-02-12
Backtrack is a very nice tool to have around thats for sure. They may have included the driver for your chipset in their kernel which solves a lot of problems for you.

If you need help post back.

---

