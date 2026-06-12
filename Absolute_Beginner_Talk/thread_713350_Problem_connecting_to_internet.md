---
title: "Problem connecting to internet"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by kkvv on 2008-03-02
Hi

I am one day old to Ubuntu - installed 7.1 yesterday. The installation was smooth.

However, I am having trouble connecting to the internet.

Ubuntu is installed on a Dell Inspiron Laptop. There is no other OS running on it now. It had XP before which did not have any problems connecting to the net. I have another laptop which runs windows from which I am typing right now. I don't have a router and there is only one cable modem box (Comcast) from which I connect the ethernet cable to the laptop(s). 

In the Network admin program, I have set to DHCP and checked the wired connection. (For some reason, the wireless adapter doesn't seem to be detected, but I will take baby steps)

The following is the output of some commands I tried:


dmk@dmk-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:91:19:BE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54688 (53.4 KB)  TX bytes:9120 (8.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9488 (9.2 KB)  TX bytes:9488 (9.2 KB)


-----------------------------------------------

dmk@dmk-laptop:~$ sudo cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       dmk-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


----------------------------------------------

dmk@dmk-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


I don't seem to find the /etc/resolv.conf file in the file system. 

Any ideas anyone?

Thanks!!

---

### Post by spiderbatdad on 2008-03-02
/etc/resolv.conf gets written by nm, so I guess It's no big surprise, still I would have thought you would have an empty file...scroll all the way down to the bottom by the files...sorry if that sounds stupid...I'm sure you've looked.

Anyway, I would set the wired connection to roaming mode. Look in the Restricted Drivers Manager for a driver.

EDIT: See this link: [http://ubuntuforums.org/archive/index.php/t-511343.html](http://ubuntuforums.org/archive/index.php/t-511343.html)
Looks very complete, and should get you going. Probably need a flash drive and use of your other computer.

---

### Post by kkvv on 2008-03-03
I will try that when I get home!

Thank you.

---

### Post by LarryJ2 on 2008-03-03
I have a Dell Inspiron E1505.  My ifconfig shows
> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:59:19:6B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22

eth1      Link encap:Ethernet  HWaddr 00:19:D2:4F:93:31
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe4f:9331/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19322 errors:87 dropped:210 overruns:0 frame:0
          TX packets:13701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15973827 (15.2 MB)  TX bytes:2626283 (2.5 MB)
          Interrupt:16 Base address:0xc000 Memory:ecfff000-ecffffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

It appears from your ifconfig output,   eth0 (your RJ45 wired connector) is not plugged into a router( or similar)  where dhcp would automatically assign an ip number  to it.  (Mine isn't either since I use the wireless chip)

I don't see your eth1 (your intel wireless chip, the Intel Corporation PRO/Wireless 2200BG ) at all.   Did you install the driver package for it?   KdeMenu ->System Settings ->Network should show  eth1 as an enabled wireless device as well as eth0.

Finally there's a package  called wicd,  which I think is far superior to Knetwork Manager when it comes to configuring wireless devices.  It's available at 
[http://wicd.sourceforge.net](http://wicd.sourceforge.net).  With my intel 3945, wicd solved several problems and has worked flawlessly since.

---

### Post by kkvv on 2008-03-04
spiderbadtad: I loaded the wireless drivers and seems like the computer is able to detect nearby wireless n/w. None of this could be connected to, though. Since they are all protected. It did not work with my windows laptop too.

But what is puzzling is the wired connection.

I connect the ethernet cable; light is always amber, never green. Ping does not work. ifconfig produces eth0 (UP BROADCAST RUNNING MULTICAST) but has errors in recv and transfers. 

I am disconnecting and connecting the ethernet cable between the 2 laptops  - trying out things which I see from the forums!

Any ideas?

---

### Post by kkvv on 2008-03-05
I got it work. Since I was changing the ethernet cable between 2 laptops in quick succession, the Ubuntu laptop was not able to pick the DHCP.

Thanks for all your help!

---

