---
title: "Connecting to the net"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by rakeshsugitharaj on 2007-12-23
Hi all,
            I m a newbie to linux. I installed the OS but i m having problems in connecting to the internet. I use a Broadband connection with ethernet. I followed all steps prescribed in ubuntu help but still aint working.Pls help

---

### Post by bumanie on 2007-12-23
It is quite likely you a suffering the problem with the ipv6 stack. This has been quite common for gutsy gibbon users.
To fix the problem, you could try a firmware upgrade for your modem. Otherwise try the following
1) In terminal type
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine. OR
2) Another way is to diable ipv6 in firefox
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true

---

### Post by jan quark on 2007-12-23
Just curiuos.. what is your hardware? Please post the results of the following commands you can type into the terminal.

lshw -C network

iwconfig

ifconfig

sudo iwlist scan

Because I have massive :) problems with my Dell lappy with the Broadcom 4311 chipset. The connection is very unstable and I am trying to figure out whats wrong. On my other desktop PC everythng worked out of the box.

---

### Post by rakeshsugitharaj on 2007-12-23
rakesh@rakesh-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: RTL-8169 Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: 2
bus info: pci@0000:01:02.0
logical name: eth0
version: 10
serial: 00:13:d4:07:a1:da
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

---

### Post by rakeshsugitharaj on 2007-12-23
rakesh@rakesh-desktop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:134:07:A1A 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:236 errors:0 dropped:0 overruns:0 frame:0
TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:16897 (16.5 KB) TX bytes:11536 (11.2 KB)
Interrupt:20 Base address:0x8000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by PeterJS on 2007-12-23
Looks like you've got a valid IP address, and looks like you've got a router, can you ping your router?

---

### Post by rakeshsugitharaj on 2007-12-23
the prob is i ve to get out of XP and get into ubuntu again and then relogin to XP... it ll take some time.. but i did go to the network settings and set up the ip,gateway,dns and subnet mask.. 
i gave the foll values..
ip-192.168.1.2
gateway-255.255.255.0
dns and subnet-192.168.1.1

should i change something in that?

---

### Post by PeterJS on 2007-12-23
The IP is correct, for right this second, but will be wrong if you ever add more devices to the network, you've got the subnet mask for the gateway, dns is right, and I assume that subnet is supposed to be the mask. If your router automatically assigns an address in XP it would be best to let it also assign you an IP and other settings in linux as well.

---

### Post by rakeshsugitharaj on 2007-12-23
rakesh@rakesh-desktop:~$ ping google.com
ping: unknown host google.com
rakesh@rakesh-desktop:~$ dig google.com

; <<>> DiG 9.4.1-P1 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 2358
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;google.com.                    IN      A

;; Query time: 1997 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Dec 23 19:55:04 2007
;; MSG SIZE  rcvd: 28

rakesh@rakesh-desktop:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.032 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.028 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.026 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.029 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.031 ms
64 bytes from 192.168.1.2: icmp_seq=6 ttl=64 time=0.030 ms
64 bytes from 192.168.1.2: icmp_seq=7 ttl=64 time=0.032 ms
64 bytes from 192.168.1.2: icmp_seq=8 ttl=64 time=0.031 ms
64 bytes from 192.168.1.2: icmp_seq=9 ttl=64 time=0.031 ms

---

### Post by rakeshsugitharaj on 2007-12-23
so should i undo all these settings.. and yes i was automatically allotted in xp! if i ve to undo the settings how do i do it?

---

### Post by rakeshsugitharaj on 2007-12-23
that ping google was asked by another person!! What does that indicate?

---

### Post by PeterJS on 2007-12-23
Huh, That's no good looks like dns isn't working. I assume you're router is working as you must be posting this from somewhere.

---

### Post by PeterJS on 2007-12-23
> **rakeshsugitharaj said:**
> that ping google was asked by another person!! What does that indicate?


Ping is pretty much the most basic diagnostic tool there is, it amount to pretty much asking someone if they exist. The reason for pining google is two fold, first it proves that DNS is working because you can get an address for google, and second that you connection is working because you can get a reply from that address.

---

### Post by rakeshsugitharaj on 2007-12-23
i m posting these msgs from windows XP installed in the same system!!?

---

