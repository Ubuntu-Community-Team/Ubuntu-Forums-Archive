---
title: "Wifi card detected?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Philistine on 2007-04-14
I installed Ubuntu 7.04 on E drive.  It seems to have detected everything apart from my Netgear WG311v3 wifi card (and my monitor, but I can fix the geforce drivers and resolution later once I have net access and can follow a thread).  I found some threads on the WG311v3 and tried to install it, but have reached a sticking point.

I tried a few things in the terminal so people could see what has happened.  If you need me to type some more commands let me know.  :)

I am a noobie to Ubuntu, so am not used to using a command line, so apologies if this is self inflicted.

Thanks in advance for your help!

Phil







phil@phil:~/WG311v3$ ndiswrapper -l 
No drivers installed 
phil@phil:~/WG311v3$ sudo ndiswrapper -i WG311v3.INF 
Installing wg311v3 
phil@phil:~/WG311v3$ sudo modprobe ndiswrapper 
phil@phil:~/WG311v3$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:06:29:99:30:59   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:12584 (12.2 KiB)  TX bytes:12584 (12.2 KiB) 
 
phil@phil:~/WG311v3$ sudo ifdown eth0 
ifdown: interface eth0 not configured 
phil@phil:~/WG311v3$  


phil@phil:~/WG311v3$ sudo ifdown eth0 
ifdown: interface eth0 not configured 
phil@phil:~/WG311v3$  
phil@phil:~/WG311v3$ sudo iwlist eth0 scan 
eth0      Interface doesn't support scanning. 
 
phil@phil:~/WG311v3$ sudo iwlist wlan0 scan 
wlan0     Interface doesn't support scanning. 
 
phil@phil:~/WG311v3$ sudo iwconfig eth0 
eth0      no wireless extensions. 
 
phil@phil:~/WG311v3$ sudo ifup eth0 
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:06:29:99:30:59 
Sending on   LPF/eth0/00:06:29:99:30:59 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping. 

phil@phil:~/WG311v3$ ping -c 1 [www.google.com](www.google.com) 
ping: unknown host [www.google.com](www.google.com)

---

### Post by N Clement on 2007-04-15
Why don't you just give us the full output of:
```
sudo iwconfig
```

(no arguments after iwconfig so we can see everything you've got)

---

### Post by Philistine on 2007-04-15
phil@phil:~$ sudo iwconfig 
Password: 
lo        no wireless extensions. 
 
eth0      no wireless extensions.

---

### Post by Austin_KW on 2007-04-15
I dont think that is your netgear
00:06:29 is an IBM device mac address

---

### Post by Philistine on 2007-04-15
I have a separate network card in my computer, so it could be that?

---

### Post by Austin_KW on 2007-04-15
is linux seeing your card
lspci

---

### Post by Philistine on 2007-04-15
Appears to be:

phil@phil:~$ sudo lspci 
Password: 
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] 
00:06.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08) 
**00:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) **
00:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge 
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) 
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

---

### Post by Austin_KW on 2007-04-15
remove the ndis driver and add it again, then check ndiswrapper -l


sudo modprobe -r ndiswrapper
sudo ndiswrapper -i WG311v3.INF
sudo modprobe ndiswrapper 
ndiswrapper -l

---

### Post by Philistine on 2007-04-15
phil@phil:~$ sudo modprobe -r ndiswrapper 
Password: 
phil@phil:~$ sudo ndiswrapper -i WG311v3.INF 
wg311v3 is already installed. Use -e to remove it 
phil@phil:~$ sudo modprobe ndiswrapper 
phil@phil:~$ ndiswrapper -l 
Installed ndis drivers: 
wg311v3 driver present, hardware present

---

### Post by Philistine on 2007-04-15
bump

---

### Post by Philistine on 2007-04-15
I'm stuck - anyone able to offer some suggestions?

Thanks

---

