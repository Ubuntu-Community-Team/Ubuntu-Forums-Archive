---
title: "able to use the airport (wifi) on my imac in ubuntu 9.1?"
date: 2010-01-01
forum: Apple Hardware Users
---

### Post by phawnex on 2010-01-01
i just successfully downloaded and installed ubuntu koala (9.10 i think...) and its a great interface. i am just having extreme difficulty trying to set up the wireless connection.

when i log back in osx, i am able to access the router and use the internet as i am doing now when i post in the forum. i am just trying to learn how to configure the wireless in ubuntu as well.

i posted in this forum instead of another one because maybe i can luck out and have someone who has successful been able to connect wirelessly on an imac, or apple laptop in ubuntu....

any help would be GREATLY appreciated. 

thanks for your time.

ps. i did some searching on the forums, how does one update or load drivers (if applicable for the built in airport wi-fi in the imac)


if push comes to shove then i may have to do a cable for ubuntu; didnt want to but if need be i will

---

### Post by gordintoronto on 2010-01-01
Drivers in Ubuntu are different from what you are used to.  Many Wireless adapters "just work."  If yours is supported, there will be a network manager icon on the top-right of your screen, near the volume control.

Right-click the network manager icon, select "edit connections," open the wireless tab, click on "add."  You will need to enter your router's ID, the type of encryption and the router's password.

---

### Post by phawnex on 2010-01-01
thanks ill check into it, and post results.

---

### Post by phawnex on 2010-01-01
its a no go...
i checked into the network manager not reading any wireless signals at all.

i went into the system>admin>hardware drivers to see wireless issues with drivers, says no propietory drivers there.

i tried to check and mess with adding a connection, but i will need to go and access the bssid and mac adress from the source computer (a windows xp)

and after browsing some similar threads to mine, someone mentioned a command called 'lspci'

i typed it and here are the results, if it helps at all?

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76XT [Mobility Radeon HD 2600 XT]
03:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 05)
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)

---

### Post by JohnAtilano on 2010-01-02
You need to download and install the broadcom driver.

Look in Administration-->Hardware Drivers (I think).  You should be offered the Broadcom and Nvidia drivers.  Download and install.  Everything will work great.

---

### Post by phawnex on 2010-01-02
i looked in the hardware drivers didnt say anything about the broadcom and nvidia drivers showing. said 'no proprietory drivers found'.   but someone gave me a tutorial ima try to install the broadcom to work.  ill post results.
 
thanks for the advice and help so far.

---

### Post by phawnex on 2010-01-03
yea the broadcom worked. my wireless is up and running. thanks for all of the assistance.

---

### Post by linuxopjemac on 2010-01-04
could you please mark this post as [SOLVED] ?

---

### Post by manzier on 2010-01-06
> **phawnex said:**
> yea the broadcom worked. my wireless is up and running. thanks for all of the assistance.

Would be helpful to the rest of us who don't know your friend with the tutorial if you posted it here so we can fix ours too

Thanks
Manzier

---

### Post by linuxopjemac on 2010-01-07
If you are having a broadcom card, you might want to try the broadcom driver from the broadcom site:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by phawnex on 2010-01-07
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

is the link manzier

---

