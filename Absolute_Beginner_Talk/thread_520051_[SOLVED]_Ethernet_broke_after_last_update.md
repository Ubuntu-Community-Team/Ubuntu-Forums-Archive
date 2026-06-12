---
title: "[SOLVED] Ethernet broke after last update"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-08-07
The last update broke my ethernet connection.  It asked for a reboot then when it came back up the ethernet connection was dead.  I connect and get an ip address but cannot ping domains or ip address.  I am still able to get online with my wireless connection.  How can I find out which were the last updates?  Here are some details of things I have tried.

> lspci | grep Ether
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

> ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:43:C6:82:EE  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe6c:82ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64574 (63.0 KiB)  TX bytes:7080 (6.9 KiB)
          Interrupt:19 



> ping yahoo.com
ping: unknown host yahoo.com


> ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

I have also tried different cables and routers.  Any ideas?  Thanks.

---

### Post by wormser on 2007-08-07
I found this [post]("http://ubuntuforums.org/showthread.php?t=345251") which solved the issue.  For some reason the firewall rules got changed.  I just ran through the Firestarter wizard and it works now.

---

