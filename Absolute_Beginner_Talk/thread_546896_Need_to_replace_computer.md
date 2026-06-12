---
title: "Need to replace computer"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by pancakelizard on 2007-09-09
SO basically my old computer caught on fire - LONG story.

Anyway, I still have one HDD (want to do RAID 5), video card, sound card, keyboard, mouse, monitor, dvdrw, cdrw and I've been pricing these parts, I would like opinions on these and also if these parts are full compatible:


board
AMD 5200 x64 x2 (combo)
214.98
[http://www.newegg.com/product/Product.asp?item=N82E16819103759](http://www.newegg.com/product/Product.asp?item=N82E16819103759)
[http://www.newegg.com/product/Product.asp?item=N82E16813131022](http://www.newegg.com/product/Product.asp?item=N82E16813131022)


ram
Crucial Ballistix 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory
109.99 (69.99 after rebate)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820146565](http://www.newegg.com/Product/Product.aspx?Item=N82E16820146565)


hard drive
Western Digital Caviar SE WD1600JS 160GB 7200 RPM 8MB Cache SATA 3.0Gb/s Hard Drive
50.99 x2 = 101.98
[http://www.newegg.com/Product/Product.asp?Item=N82E16822144415](http://www.newegg.com/Product/Product.asp?Item=N82E16822144415)


case
Antec Performance One P180B Black 0.8mm cold rolled steel for durability through the majority of chassis 1.0mm
129.99
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811129017](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129017)


power supply
Thermaltake Purepower W0100RU ATX 12V 2.0 500W Power Supply 115/230 V UL, CUL, TUV, FCC, and CB certification
59.99 (39.99 after rebate)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153052](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153052)


misc...
hdd connector cables
2.89 x2 = 5.78
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812123132](http://www.newegg.com/Product/Product.aspx?Item=N82E16812123132)

floppy drive
7.99
[http://www.newegg.com/Product/Product.aspx?Item=N82E16821103116](http://www.newegg.com/Product/Product.aspx?Item=N82E16821103116)

heat sink & fan
27.95
[http://www.catalog800.com/.sc/ms/dd/ee/20076/KINGWIN%20KA-9228%20COPPER%20CPU%20FAN%20FOR%20INTEL%20AND%20AMD%20CPU](http://www.catalog800.com/.sc/ms/dd/ee/20076/KINGWIN%20KA-9228%20COPPER%20CPU%20FAN%20FOR%20INTEL%20AND%20AMD%20CPU)

thermal compound
5.99
[http://www.newegg.com/Product/Product.asp?Item=N82E16835100007](http://www.newegg.com/Product/Product.asp?Item=N82E16835100007)

---

### Post by pancakelizard on 2007-09-09
-bump-

i'm really want to make sure im not getting anything that won't be compatible due to driver issues. please look into.

---

### Post by Hossie on 2007-09-09
Aside from the motherboard there are no components that could not be "supported". The board has a nforce-chipset. For windows-pleasures that might be really good, but under linux its normally not that good. If you really want an AMD processor there is probably not a better choice, but if you could switch to an Intel processor, get a board with intel chipset. Intel is releasing all drivers (including grahpics and wlan) as opensource.

&#8364;: You should also google for PATA and SATA (probably nvidia, but you dont know) chipsets and look for linux support for them.

---

### Post by LowSky on 2007-09-09
its an asus board with an amd processor... i dont see any problems.
everything else is generic and wont cause any prolems either

---

### Post by LowSky on 2007-09-09
> **Hossie said:**
> Intel is releasing all drivers (including grahpics and wlan) as opensource.

AMD just announce it is doing the same with its ATI drivers as well.

I have never had a problem with my Nvidia drivers (3 computers running Ubuntu and Xubuntu just fine)

---

### Post by rsambuca on 2007-09-09
I think the thermal compound you have chosen may have compatibility issues with older linux kernels, but you should be OK with Feisty.

:popcorn:

---

### Post by Hossie on 2007-09-09
> **LowSky said:**
> AMD just announce it is doing the same with its ATI drivers as well.

I have never had a problem with my Nvidia drivers (3 computers running Ubuntu and Xubuntu just fine)

We're not talking about the graphics card (which will be fine whatever you choose, Nvidia > ATI for now), but about the chipset and PATA and SATA controllers and the ethernet controller. Nvidia doesnt release specs about their controllers, so for nforce-chipsets there is only a reverse-engineered "forcedeth" driver for their lan controllers for example.

---

### Post by Aishiko on 2007-09-09
I believe under fiesty that fan is detected as a [Sensenich wood prop W74FM-49]("http://www.aircraftspruce.com/pdf/2008Individual/Cat08177.pdf")  But they sya they'll have that fixed in gusty.

---

### Post by Majorix on 2007-09-09
You have to either be a comp eng with the necessary tools to test the hardware compatibility between each other or have an overheating/self-restarting/dying computer.

I would go with a comp that is pre-built by some company.

---

### Post by Officer Dibble on 2007-09-09
> **pancakelizard said:**
> -bump-

i'm really want to make sure im not getting anything that won't be compatible due to driver issues. please look into.

You won't have driver issues with any of that kit... it's all core hardware. Looking at what you have listed there the only thing that *might* remotely cause a problem would be the motherboard's integrated graphics card - depending on what it is for that board... but if you buy yourself a proven Nvidia to fit, all should go well.

Tis up to you... :)

---

### Post by Wiebelhaus on 2007-09-09
> **Hossie said:**
> Aside from the motherboard there are no components that could not be "supported". The board has a nforce-chipset. For windows-pleasures that might be really good, but under linux its normally not that good. If you really want an AMD processor there is probably not a better choice, but if you could switch to an Intel processor, get a board with intel chipset. Intel is releasing all drivers (including grahpics and wlan) as opensource.

&#8364;: You should also google for PATA and SATA (probably nvidia, but you dont know) chipsets and look for linux support for them.

I'll have to politely disagree , out of the 5 Ubuntu machines in my house all have MSI boards with Nforce chipsets , I haven't had a single issue. 

I'm a hardcore loyalist to:

MSI
Nvidia
Antec
LG
Kingston
Western Digital (I've seen a many failures on the bench , But have never experienced it myself with this company , but that's the bane of the current hard drive tech , but with 1-3 year no questions asked warranty , they can be trusted)

Haven't had any issues with these manufacturers , But since the ATI/AMD merge , I'm hearing & reading allot of nice things , I haven't touched a ATI product since a horrible expirence with the 4000 series cards , but the next card I buy will be ATI , matter of fact the X1950 Pci-E 256mb+ cards are a killer deal right now.

---

### Post by Krydahl on 2007-09-09
The P182 is a great case, but you should be aware it is an unusual layout. The PSU fits at the bottom of the case in a separate compartment (that also has a drive cage). The idea is that the PSU isn't getting fed hot air straight off the CPU/GPU and so runs cooler and quieter. It's a good design, but it does mean that the PSU is further away from the mobo than usual. Some PSU don't have cables long enough to reach the main power sockets as a result.

I did a quick search on the Thermaltake you're thinking of, but couldn't find an mention of the length of the cables. Not a driver problem, but maybe worth being aware of.

---

### Post by therandman on 2007-09-09
> **rsambuca said:**
> I think the thermal compound you have chosen may have compatibility issues with older linux kernels, but you should be OK with Feisty.

:popcorn:

:lolflag:

---

