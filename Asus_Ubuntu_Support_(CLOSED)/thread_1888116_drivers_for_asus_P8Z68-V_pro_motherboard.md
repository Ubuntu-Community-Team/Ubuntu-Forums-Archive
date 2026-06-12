---
title: "drivers for asus P8Z68-V pro motherboard"
date: 2011-11-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by shadeed on 2011-11-28
i'm building a new system with asus MB -P8Z68-V pro- intel i7 2600k, but once i installed ubuntu 10.04 LTS i couldn't install the drivers, the main problem that i could't even connect to internet to check for them cause i need the NIC driver, please help

---

### Post by m.suzuki on 2011-12-03
I used another Z68 motherboard from Asus to build my computer.
It connected to the net immediately after I installed Ubuntu 11.10, without any additional installation.
However, no software for Linux can be found in the Asus website (this is also the case with P8Z68-V pro). So I don't even know if the CPU clock is controlled at all.

---

### Post by Robertjm on 2011-12-09
Did you ever resolve this? Working on this as we speak and it is driving me nuts!!

> **shadeed said:**
> i'm building a new system with asus MB -P8Z68-V pro- intel i7 2600k, but once i installed ubuntu 10.04 LTS i couldn't install the drivers, the main problem that i could't even connect to internet to check for them cause i need the NIC driver, please help

---

### Post by bluexrider on 2011-12-09
ASUS P8Z68-V PROASUS P8Z68-V PRO is a motherboard. This product is available from ASUS. The ASUS P8Z68-V PRO has been tested via the Phoronix Test Suite in the configurations listed below.

Operating Systems
Ubuntu 11.04
Ubuntu 9.10
Arch
Debian testing
Kernels2.6.31-14-generic
2.6.38-8-generic2.6.39
OpenGL Drivers 3.2.0 
NVIDIA 190.424.1.0 
NVIDIA 275.09.074.1.0 
NVIDIA 270.41.062.1 
Mesa 7.10.22.1 
Mesa 7.10.3
Display Servers
X Server 1.10.1
X Server 1.10.2

[http://openbenchmarking.org/s/ASUS%20P8Z68-V%20PRO](http://openbenchmarking.org/s/ASUS%20P8Z68-V%20PRO)

---

### Post by gordintoronto on 2011-12-10
> **shadeed said:**
> i'm building a new system with asus MB -P8Z68-V pro- intel i7 2600k, but once i installed ubuntu 10.04 LTS i couldn't install the drivers, the main problem that i could't even connect to internet to check for them cause i need the NIC driver, please help

Huh? Drivers in Linux are completely different from drivers in Windows.

Don't install an old version of Linux with a new motherboard.

---

### Post by bluexrider on 2011-12-10
> **gordintoronto said:**
> Huh? Drivers in Linux are completely different from drivers in Windows.

Don't install an old version of Linux with a new motherboard.
God, grant me the serenity
to accept the things I cannot change;
the courage to change the things I can;
and the wisdom to know the difference 
between Linux and Windows.

---

### Post by rick6655 on 2011-12-12
> **shadeed said:**
> i'm building a new system with asus MB -P8Z68-V pro- intel i7 2600k, but once i installed ubuntu 10.04 LTS i couldn't install the drivers, the main problem that i could't even connect to internet to check for them cause i need the NIC driver, please help

Older e1000e drivers aren't compatible with the NIC on the Sandy Brdige boards. You could downloadload / copy from a newer release and modprobe it or download from Intel and follow instructions to install. [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3299&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3299&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A")

---

### Post by JakartaDean on 2012-01-20
I've got one of these also, using it to build the computer that lasts me the rest of my life (I hope!).  I'm curious if anyone was able to get the on-board RAID working, as that's my current barrier.  I can see on the net that the Marvell controller (not even sure which one that is, manual isn't helpful) doesn't play nicely with linux.  I'm considering adding a RAID card, but that seems a waste.

Thanks in advance for any help or shared experiences.

Dean

---

### Post by sw33t on 2012-08-10
Hi!

Anyone had any luck with getting suspend (standby) working on P8Z68-V pro with Ubuntu 12.04 LTS? I tried switching to kernel 3.4 but still no luck. It doesn't suspend, it just freezes and I need to do a hard reset.

Thanks!

---

