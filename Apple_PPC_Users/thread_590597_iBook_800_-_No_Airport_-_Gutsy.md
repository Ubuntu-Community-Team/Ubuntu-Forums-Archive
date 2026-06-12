---
title: "iBook 800 - No Airport - Gutsy"
date: 2007-10-24
forum: Apple PPC Users
---

### Post by reidbold on 2007-10-24
So dual usb macbook with an airport card, known to work in a previous osx installation. 

The airport, hermes, and orinoco module have loaded and created the wireless device eth1. the device is in the network-manager, any attempt to connect fails with no error messages.

running iwlist eth1 -scan 
here's ifconfig, iwconfig and some stuff from the kernel

I'm out of ideas, help please?

> 
lsmod |grep airport
airport                 7808  0 
orinoco                47348  1 airport
hermes                  9024  2 airport,orinoco


 iwlist eth1 scanning 
eth1      No scan results



ifconfig
eth1      Link encap:Ethernet  HWaddr 00:30:65:15:E8:B6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:57 

eth1:avah Link encap:Ethernet  HWaddr 00:30:65:15:E8:B6  
          inet addr:169.254.8.104  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:57 

iwconfig
eth1      IEEE 802.11b  ESSID:"330rulez"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


kern.log
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452030] eth1: Hardware identity 0005:0001:0001:0002
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452146] eth1: Station identity  001f:0001:0004:0010
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452155] eth1: Firmware determined as Lucent/Agere 4.16
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452161] eth1: Ad-hoc demo mode supported
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452233] eth1: MAC address 00:30:65:15:E8:B6
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452317] eth1: Station name "HERMES I"
Oct 24 22:43:27 rmiller-laptop kernel: [   54.452598] eth1: ready
Oct 24 22:43:27 rmiller-laptop kernel: [   54.454503] airport: Card registered for interface eth1
Oct 24 22:43:30 rmiller-laptop kernel: [   64.265483] eth1: New link status: Disconnected (0002)
Oct 24 22:45:41 rmiller-laptop kernel: [  194.983412] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 24 22:48:01 rmiller-laptop kernel: [  335.552587] eth1: New link status: Disconnected (0002)


---

