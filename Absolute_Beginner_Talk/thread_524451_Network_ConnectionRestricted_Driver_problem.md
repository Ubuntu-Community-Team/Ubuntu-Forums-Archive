---
title: "Network Connection/Restricted Driver problem"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by riskpusher4life on 2007-08-13
Hi, I recently installed Ubuntu in my system which has an Nvidia Graphics Card ( 5500) agp card and I am not able to enable the restricted driver in it. It is asking me to download the Nvidia drivers from the website  

I am [B]using BSNL broaband internet from India and I have been provided with an internal ADSL Modem that is from a company called "sasken".
and I am not able to use my Sasken Modem for Internet connectivity which is a PPPoE modem.
I tried    sudo PPPOEconf and it said that either my ethernet connections were not completely connected or that some other pppoe connection is controlling my internet card. [/B]

also is my connection a static one or is it a modem connection which requires dial up access .
ALso i really need the 3d effects on my system which will not be enabled unless the Nvidia driver is in place.
THanks.

---

### Post by Kobalt on 2007-08-13
Hello,

Can you please post here the output of the following command lines, so that we can identify precisely your modem : ```
lspci
sudo lshw -C network
```

---

### Post by riskpusher4life on 2007-08-13
Yeah Kobalt thanks for looking up my problem I will get back to you in a bit surely...meanwhile can you please suggest something to do with the restricted driver on my Nvidia graphics card?
Thanks.

---

### Post by Kobalt on 2007-08-13
What you can do is download that driver from windows or another internet connected computer from [http://packages.ubuntu.com](http://packages.ubuntu.com) then copy it in your Ubuntu. You should look for *nvidia-glx-new*, given your card. Once you have downloaded that file (a Debian package), double-click it. It will install automatically. Then run this tool from the Terminal to update your configuration and you'll be done (after a reboot) : ```
sudo nvidia-xconfig
```

---

### Post by kv_abhiram on 2007-08-13
i have downloaded the envy -dep package frm the net thru windows-xp
 but the problem is it is askin to download the entire package from the net
and more over as far as i know nvidia drivers will b updated once it is done

ny suggestions ????

---

### Post by Kobalt on 2007-08-13
If yo are a beginner user of Ubuntu I recommend you not to use Envy to install your drivers: it installs the latest and possibly unstable version of the drivers and it can lead to a temporary crash of your system. You would need to reconfigure it through the command line. 
If you wish to install the drivers without internet connection in Ubuntu I advise to follow the steps I give above instead. 
Plus the drivers will be update automatically by the Update Manager when one is available.

---

### Post by kv_abhiram on 2007-08-13
EVEN if i download the nvidia-glx-new .deb package uve mentioned
im not able to install it
its giving some error

---

### Post by kv_abhiram on 2007-08-13
THIS IS THE ERROR IM GETTING


These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server and supports the
newer GeForce, nForce and Quadro families of NVIDIA chipsets.
AGP, TV-out and flat panel displays are also supported.
If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package instead of this one. If you have a GeForce4, you may need the nvidia-glx package.
To enable the driver, run "sudo nvidia-glx-config enable".

---

### Post by kv_abhiram on 2007-08-13
DETAILS OF THE MODEM WE ARE TALKIN ABOUT




*-network:0 UNCLAIMED 
description: Network controller 
physical id: 9 
bus info: pci@00:09.0 
version: 01 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list 
configuration: latency=64 maxlatency=16 mingnt=1 
resources: iomemory:febf0000-febfffff irq:11 
*-network:1 
description: Ethernet interface 
product: VT6102 [Rhine-II] 
vendor: VIA Technologies, Inc. 
physical id: 12 
bus info: pci@00:12.0 
logical name: eth0 
version: 78 
serial: 00:16:ec:94:e4:d2 
size: 10MB/s 
capacity: 100MB/s 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s 
resources: ioport:ee00-eeff iomemory:febef800-febef8ff irq:18

---

### Post by kv_abhiram on 2007-08-13
Now Can U Help Me Out With The Internet Thing

---

### Post by kv_abhiram on 2007-08-20
hELOOOOOOOOO
ANY BODY THERE ???????????

---

