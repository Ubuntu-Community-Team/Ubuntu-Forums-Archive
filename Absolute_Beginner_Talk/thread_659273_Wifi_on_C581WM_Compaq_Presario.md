---
title: "Wifi on C581WM Compaq Presario"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Avant Gardener on 2008-01-05
My laptop has the following network adapters:

"Realtek RTL8139/810x Family Fast Ethernet NIC"
"Broadcom 802.11b/g WLAN"

My router is a Belkin 54 WirelessG...

When I run ifconfig, iwconfig, and lspci, I get the following results:

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1B:38:8C:92:CD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 




ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311" 
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 




ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 


I'm having trouble connecting to my wireless network. Further help would be appreciated...

---

### Post by exneo002 on 2008-01-05
just physically remove your card and use a belkin

---

### Post by p_quarles on 2008-01-05
Most Broadcom cards require you to use the Windows-based driver with an application called NDISwrapper. I was able to find a link with relatively easy-to-follow instructions for this. 

[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

Take note, though, that it looks like you have a slightly different model from the one discussed in this thread. Be forewarned, too, that Broadcom cards can be a pain to get working correctly. 

If you're patient, though, you'll get it up and running.

---

### Post by Presto123 on 2008-01-05
If you get the driver when you go into your "Restricted Drivers Manager" (Ubu 7.10) and use the internet to install it (Check box after you select the device). Is this what you get? My Compaq C500 with the Broadcom worked flawlessly this way.

---

### Post by stormdragon2976 on 2008-04-26
> **Presto123 said:**
> If you get the driver when you go into your "Restricted Drivers Manager" (Ubu 7.10) and use the internet to install it (Check box after you select the device). Is this what you get? My Compaq C500 with the Broadcom worked flawlessly this way.
Our Compaq has a fresh copy of Ubuntu 8.04 on it. We were able to go into the hardware drivers and enable the wireless driver. The light came on, but it will not connect to the internet. I even tried resetting the Belkin54G to it's defaults. Still no luck. When I did ifconfig, it said could not find host I think. It's wireless card is a 802.11b/g wireless lan.
Thanks for any help
Storm

---

