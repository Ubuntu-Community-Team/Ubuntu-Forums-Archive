---
title: "Still Can’t connect DWL-AG530 Wireless Card"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by jlr4u on 2006-12-26
I am still not able to connect myDWL-AG530 wireless card with 4 days of tying one thing after another and I am about to give drink my last cup of Ubuntu.

Here is my load procedure to attempt to use Ndiswrapper.
Note: I do not have internet connection so I used a USB Key for downloads.
________________________________________________________
Load Ubuntu 6.10
Download Diswrapper files below to a USB Key
Load ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb	to usb key
Load ndiswrapper-common_1.18-1ubuntu2_all.deb 		to usb key

Open up USB Key folder and double click on each file to install

From Terminial Code: ndiswrapper -i		To Verify Load

sudo gedit /etc/modprobe.d/blacklist
	add the following line at the end of the file and save:
blacklist ath_pci

	Make sure the wireless card (ath0 in my case) is not active:
sudo ifconfig ath0 down

	Remove the Madwifi module from memory:
sudo modprobe -r ath_pci


gksudo nautilus
Copy DLink Drivers folder from Cd to usr directory
Rename  user/Drivers to  user/Drivers DW530_Drivers
cd /usr		--you must be in usr folder
ndiswrapper -i DW530_Drivers/NetA3AB.inf
ndiswrapper -m
modprobe ndiswrapper
ndiswrapper -l

sudo gedit /etc/modules
	add the following line at the end of the file and save:
ndiswrapper

sudo gedit /etc/network/interfaces
add the following at the end of the file and save:

auto wlan0
iface wlan0 inet dhcp
wireless-essid JLR_NET

_____END OF LOAD PROCEDURE_________
__________ Detail Scripts on Results________
jlr@Jlr-PVR:~$ sudo -i
Password:
root@Jlr-PVR:~# lshw -C network
  *-network               
       description: Wireless interface
       product: AR5006X 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 8
       bus info: pci@01:08.0
       logical name: ath0
       version: 01
       serial: 00:17:9a:b5:ae:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.22 firmware=D-Link,08/24/2005,4.1.2.72 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fdff0000-fdffffff irq:58
************************************
root@Jlr-PVR:~# ndiswrapper -l
Installed drivers:
neta3ab         driver installed, hardware present 
************************************
root@Jlr-PVR:~# ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:17:9A:B5:AE:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Memory:fdff0000-fe000000 

eth0      Link encap:Ethernet  HWaddr 00:14:2A:6B:92:D8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
************************************
root@Jlr-PVR:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11b  ESSID:"JLR_NET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:FACE-00CA-FE   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
************************************
root@Jlr-PVR:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 5748
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:17:9a:b5:ae:20
Sending on   LPF/ath0/00:17:9a:b5:ae:20
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
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
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/ath0/00:17:9a:b5:ae:20
Sending on   LPF/ath0/00:17:9a:b5:ae:20
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping
************************************

Please Help, I am on my last cup of Ubuntu
************************************

---

