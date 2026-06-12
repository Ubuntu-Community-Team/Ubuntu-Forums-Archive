---
title: "Help with USB Wireless RT73"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by mrglimm on 2008-01-16
I know, there are many posts on this.  I still don't see what I'm doing wrong though.  I seem to have gotten the RT73 installed with the monkey drivers, but I am missing something.  I don't think it is active or something.  When I look at the Net Mngr. it doesn't list any wireless AP's.   Here are the outputs for anyone to help with. My only requirement is to not use NDISwrapper.  I'd like to learn the real way of doing this instead of just a shortcut...

darius@darius-desktop:~$ lsusb
Bus 005 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
darius@darius-desktop:~$ 


darius@darius-desktop:~$ sudo lshw -C network
[sudo] password for darius:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 10
       serial: 00:0d:87:ae:43:96
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN




darius@darius-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0




darius@darius-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:AE:43:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


lshw -c network says wireless network DISABLED??
lsusb obiously shows it plugged in, but ifconfig doesn't agree?  Thanks in advance for everyone's help..

---

### Post by Hightide on 2008-01-19
> **mrglimm said:**
>   When I look at the Net Mngr. it doesn't list any wireless AP's.

You should try the 'network and wireless' forum on this one.

ok. There is a body of opinion that indicates that NM gives some weird results. Others have tried an alternative Manager called WICID  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=531268&highlight=wicid](http://ubuntuforums.org/showthread.php?t=531268&highlight=wicid)

give it a go

:)

---

### Post by mrglimm on 2008-01-19
Thanks, I did eventually get this working with Rutilt, thanks, I don't know how to close this post...

---

