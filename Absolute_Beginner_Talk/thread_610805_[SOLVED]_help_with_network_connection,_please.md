---
title: "[SOLVED] help with network connection, please"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by m@@dL3s on 2007-11-12
I am brand new to Ubuntu, and cannot get my computer connected to the wireless network here at home. I've read thru several posts here and tried various options, included enabling WEP instead of WAP on the router.  

Here is the information after running
lspci
sudo lshw -C network
dmesg | grep eth

-----
lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01) 
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
10:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01) 
--------
 *-network DISABLED      
       description: Wireless interface 
       product: BCM4310 UART 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@10:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:1a:73:50:ee:74 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g 
       resources: iomemory:f4000000-f4003fff irq:17 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: e 
       bus info: pci@02:0e.0 
       logical name: eth0 
       version: 02 
       serial: 00:17:a4:e0:11:86 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s 
       resources: iomemory:f4108000-f4109fff irq:16 
--------------
[   18.604709] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots. 
[    7.112000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:17:a4:e0:11:86 
[  260.872000] ADDRCONF(NETDEV_UP): eth0: link is not ready 
-----

I can see that the wireless is not enabled, but do not see how to do this. I've been using Network manager.  The ESSID is correct, typed correctly upper/lower case. 
I've set a WEP key, and tried both DHCP and a static IP address. Neither worked, then after some searching, I found the list of wireless routers accepted by Linux and then downloaded the files listed here for my wireless router:

[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)

using the command shown in Terminal

sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

I get "command not found". Ubuntu can't find the files? They are extracted on the desktop right now. Should they be elsewhere?

I am dual-booting with Vista, and have no trouble connecting to the wireless that way, so it is apparently the configuration in Ubuntu.   I've seen [this post]("http://ubuntuforums.org/showthread.php?t=525464") that suggest using wifi-radar, but I can't install thru Synaptic if I have no internet connection.  Thank you for any help.

---

### Post by bumanie on 2007-11-12
This may not be of much help, but may give you a start. I think if the files are on your desktop you need to type 'cd ~ /Desktop' in terminal (no quote marks) --> this will change your directory to desktop.

---

### Post by mkoehler on 2007-11-12
m@@dL3s,

     Can you post the output of the following commands here:

```
sudo /etc/init.d/networking restart
sudo iwconfig eth1
sudo iwlist eth1 scan
```


Also, could you post the contents of your /etc/network/interfaces file.  That should help us with debugging your individual situation.

Cheers!

---

### Post by m@@dL3s on 2007-11-12
Thanks for the reply. Here you go:

sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                                                                                     
 eth2: ERROR while getting interface flags: 
 No such device 
 There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416 
 Internet Systems Consortium DHCP Client V3.0.4 
 Copyright 2004-2006 Internet Systems Consortium. 
 All rights reserved. 
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
SIOCSIFADDR: No such device 
eth2: ERROR while getting interface flags: No such device 
eth2: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up eth2. 
ath0: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
SIOCSIFADDR: No such device 
ath0: ERROR while getting interface flags: No such device 
ath0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up ath0. 
wlan0: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 Copyright 2004-2006 
Internet Systems Consortium. All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 
SIOCSIFADDR: No such device 
wlan0: ERROR while getting interface flags: No such device 
wlan0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up wlan0. 
Error for wireless request "Set Encode" (8B2A) :     
invalid argument "mypassword". 
                                                                                                                                                      [ OK ] 
:~$ sudo iwconfig eth1 eth1      
IEEE 802.11g  ESSID:off/any             
Mode:Managed  Frequency:2.462 GHz  
Access Point: Not-Associated              
Bit Rate=54 Mb/s   Tx-Power:32 dBm              
RTS thr=2347 B   Fragment thr=2346 B              
Encryption key:off           
Power Management:off           
Link Quality:0  
Signal level:0  
Noise level:0           
Rx invalid nwid:0  
Rx invalid crypt:0  
Rx invalid frag:0           
Tx excessive retries:0  
Invalid misc:0   
Missed beacon:0 
 
sudo iwlist eth1 scan eth1      
Scan completed :           
Cell 01 - Address: 00:90:4C:7E:00:64                     
ESSID:"TheFam"                     
Protocol:IEEE 802.11g                     
Mode:Managed                     
Frequency:2.462 GHz (Channel 11)                     
Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm                     
Encryption key:on                     
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                               
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s                               
12 Mb/s; 48 Mb/s                     
Extra:bcn_int=100                    
Extra:atim=0                     
IE: WPA Version 1                         
Group Cipher : TKIP                          
Pairwise Ciphers (1) : TKIP                          
Authentication Suites (1) : PSK 
            
Cell 02 - Address: 00:90:4C:7E:00:6E
ESSID:"NETGEAR"                     
Protocol:IEEE 802.11g                     
Mode:Managed                     
Frequency:2.462 GHz (Channel 11)
Quality:6/100  
Signal level:-92 dBm  
Noise level:-96 dBm                     
Encryption key:off                     
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                               
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s                               
12 Mb/s; 48 Mb/s                     
Extra:bcn_int=100                     
Extra:atim=0

---

### Post by m@@dL3s on 2007-11-12
forgot interfaces (that's not my real password BTW):


auto lo 
iface lo inet loopback  
 
auto eth2 
iface eth2 inet dhcp 
 
auto ath0 
iface ath0 inet dhcp 
 
auto wlan0 
iface wlan0 inet dhcp  
 
 
iface eth1 inet static 
wireless-essid TheFam 
wireless-key mypassword 
address 192.168.1.1 
netmask 255.255.255.0 
gateway 192.168.1.1 
 
 
 
auto eth1

---

### Post by m@@dL3s on 2007-11-13
Just reporting in that I have successfully connected, after many hours.

The document here
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
is what helped me finally succeed.

Also I would note that on one of the articles/blogs I read in this process, only one pointed this out:
```
user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

```

In the above lines, the punctuation is the backtick, in the upper left of your keyboard, *not* an apostrophe. I did not copy the link on this information, which was an article on a website, not here, sorry, but it was the only place I came across this information in the posts here that provided those lines of code. I never used the backtick before, ever, and would never have noticed that tiny little thing was *not* an apostrophe, so hopefully this might help someone else here.

Also I would not that there were small differences in some of the steps in the tutorial compared to my results, so I'm not sure this will still be working tomorrow :) but at least I'm on now. I would note them but there was a fair amount of trial and error getting it going...

---

