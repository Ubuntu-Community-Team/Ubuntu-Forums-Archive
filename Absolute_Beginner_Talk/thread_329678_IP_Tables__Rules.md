---
title: "IP Tables / Rules"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by ubu_n00b69 on 2007-01-02
I am seeing my DSL Modem talking out above Port 30000 to a few constant IP Addresses.
I also don't know if the IP Logfile I am looking at is correct either. There just seems to be way too much traffic.

Since I am pretty new to Linux, how would I find a Trojan? I have installed Clam AV, but it seems you have to pick a certain folder or file and scan it. 

I have 2 Desktops and 1 Laptop with Ubuntu, and my Kid's Box which has XP.
When I check the Firewall program on my Kid's Box, nothing seems unusual.
I have my neighbor hooked up through a Bridge, and he has the OTHER OS, but his Firewall is showing a TON of action.

My WAN IP is DHCP from Alltel. I have a Netgear WGR614 Wireless Router, and a Linksys WAP11.

192.168.0.1 is the Gateway
192.168.254.254 is the Modem Management Page and 192.168.254.1 is the first available address of the Modem.

Here are small portions of what I am seeing.

_**This from the Siemens Speedstream Modem:**_

0000-00-00 22:42:29 E |Firewall             |P:11:322 TCP 192.168.254.1:33101 -> 82.165.133.232:80  len=44  id=18385  DF=0 MF=0  byte-off=0

0000-00-00 22:42:29 E |Firewall             |P:11:322 TCP 192.168.254.1:56465 -> 68.142.110.220:80  len=44  id=45034  DF=0 MF=0  byte-off=0

0000-00-00 22:42:29 E |Firewall             |P:11:322 TCP 192.168.254.1:60958 -> 208.111.153.172:80  len=44  id=45801  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:38749 -> 68.142.72.29:80  len=44  id=62425  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:59137 -> 69.28.159.16:80  len=44  id=57641  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:41167 -> 68.142.121.14:80  len=44  id=48930  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:41028 -> 68.142.121.152:80  len=44  id=30208  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:43948 -> 69.28.159.225:80  len=44  id=37139  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:50964 -> 208.111.148.30:80  len=44  id=30304  DF=0 MF=0  byte-off=0

0000-00-00 22:42:30 E |Firewall             |P:11:322 TCP 192.168.254.1:37897 -> 204.2.208.48:80  len=44  id=28172  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:36619 -> 66.232.110.173:80  len=44  id=47684  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:49908 -> 66.11.50.67:80  len=44  id=25156  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:36479 -> 38.101.216.149:80  len=44  id=37382  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:37901 -> 204.2.208.48:80  len=44  id=52932  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:55213 -> 68.142.91.205:80  len=44  id=63924  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:60971 -> 208.111.153.172:80  len=44  id=5856  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:53886 -> 208.109.90.9:80  len=44  id=53869  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:53887 -> 208.109.90.9:80  len=44  id=60559  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:40507 -> 208.111.153.239:80  len=44  id=28638  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:36583 -> 68.142.91.76:80  len=44  id=29873  DF=0 MF=0  byte-off=0

0000-00-00 22:42:31 E |Firewall             |P:11:322 TCP 192.168.254.1:52000 -> 204.2.208.39:80  len=44  id=4005  DF=0 MF=0  byte-off=0

0000-00-00 22:42:32 E |Firewall             |P:11:322 TCP 192.168.254.1:55818 -> 204.2.208.71:80  len=44  id=39346  DF=0 MF=0  byte-off=0

**_This is from /var/log/kern.log:_**

Jan  1 09:47:03 localhost kernel: [17230594.772000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7773 PROTO=UDP SPT=5911 DPT=137 LEN=58 
Jan  1 09:47:04 localhost kernel: [17230595.900000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7774 PROTO=UDP SPT=5911 DPT=137 LEN=58 
Jan  1 09:47:05 localhost kernel: [17230596.764000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7775 PROTO=UDP SPT=5912 DPT=137 LEN=58 
Jan  1 09:47:06 localhost kernel: [17230597.892000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7776 PROTO=UDP SPT=5912 DPT=137 LEN=58 
Jan  1 09:47:07 localhost kernel: [17230598.760000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7777 PROTO=UDP SPT=5913 DPT=137 LEN=58 
Jan  1 09:47:08 localhost kernel: [17230599.884000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7778 PROTO=UDP SPT=5913 DPT=137 LEN=58 
Jan  1 09:48:25 localhost kernel: [17230676.548000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7791 PROTO=UDP SPT=5920 DPT=137 LEN=58 
Jan  1 09:48:26 localhost kernel: [17230677.652000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7792 PROTO=UDP SPT=5920 DPT=137 LEN=58 
Jan  1 09:48:27 localhost kernel: [17230678.544000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7793 PROTO=UDP SPT=5921 DPT=137 LEN=58 
Jan  1 09:48:28 localhost kernel: [17230679.652000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7794 PROTO=UDP SPT=5921 DPT=137 LEN=58 
Jan  1 09:48:29 localhost kernel: [17230680.540000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7795 PROTO=UDP SPT=5922 DPT=137 LEN=58 
Jan  1 09:48:30 localhost kernel: [17230681.640000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7796 PROTO=UDP SPT=5922 DPT=137 LEN=58 
Jan  1 09:49:46 localhost kernel: [17230758.328000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7809 PROTO=UDP SPT=5929 DPT=137 LEN=58 
Jan  1 09:49:48 localhost kernel: [17230759.468000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7810 PROTO=UDP SPT=5929 DPT=137 LEN=58 
Jan  1 09:49:48 localhost kernel: [17230760.324000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7811 PROTO=UDP SPT=5930 DPT=137 LEN=58 
Jan  1 09:49:50 localhost kernel: [17230761.460000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7812 PROTO=UDP SPT=5930 DPT=137 LEN=58 
Jan  1 09:49:50 localhost kernel: [17230762.316000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7813 PROTO=UDP SPT=5931 DPT=137 LEN=58 
Jan  1 09:49:52 localhost kernel: [17230763.416000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7814 PROTO=UDP SPT=5931 DPT=137 LEN=58 
Jan  1 09:51:08 localhost kernel: [17230840.108000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7827 PROTO=UDP SPT=5938 DPT=137 LEN=58 
Jan  1 09:51:09 localhost kernel: [17230841.216000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7828 PROTO=UDP SPT=5938 DPT=137 LEN=58 
Jan  1 09:51:10 localhost kernel: [17230842.100000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7829 PROTO=UDP SPT=5939 DPT=137 LEN=58 
Jan  1 09:51:11 localhost kernel: [17230843.212000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7830 PROTO=UDP SPT=5939 DPT=137 LEN=58 
Jan  1 09:51:12 localhost kernel: [17230844.096000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7831 PROTO=UDP SPT=5940 DPT=137 LEN=58 
Jan  1 09:51:13 localhost kernel: [17230845.232000] Inbound IN=eth1 OUT= MAC=00:06:25:ab:eb:63:00:09:5b:52:b7:24:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=7832 PROTO=UDP SPT=5940 DPT=137 LEN=58 

And it goes on and on and on and on.

I have not felt a performance hit as of yet.

I will keep reading and searching.

Thank you for your time.

Mike

---

### Post by zigford on 2007-01-02
Hi Mike,

I think some of the traffic you are seeing is normal...

I will analyse the log for you


0000-00-00 22:42:29 E |Firewall |P:11:322 TCP 192.168.254.1:33101 -> 82.165.133.232:80 len=44 id=18385 DF=0 MF=0 byte-off=0

This output is telling you that the computer 192.168.254.1 is sending a packet with a source port of 33101 to the computer 82.165.133.232 with a destination port of 80 (Usually web traffic)

I think you may be getting confused with the difference of source and destination ports.  When an application wants to communicate with another server or service on the internet, it sends that communication from an "Unprivileged Port" (Any port above 1024), to its destination port of (in this case) 80.

So that log describes a computer accessing a web page.

I can't tell you what the second log means, but if you want an idea of network traffic on your linux box, use "tcpdump -i *interface*"

This command will tell you all traffic in and out on that box.  You can also get "windump" for windows which will behave in the same way as tcpdump.

Good luck

---

### Post by wirelessmonkey on 2007-01-02
Limelightnetworks (the destination of most of your log entries) is a file host, generally for DRM'd content.  My guess right off the top is that you or your bridged companion are using filesharing software, as limelight...'  also likes to play policeman for the **AA.  I highly suggest that unless you are absolutely certain that you are in the legal right, you either stop filesharing OR.... if you're MOSTLY sure, or prefer your right to privacy regardless, you use an application such as PeerGuardian2, and it's peers.


Best of Luck

---

### Post by ubu_n00b69 on 2007-01-02
Thank you for the Tips:) 
I will continue my Quest for Knowledge.

I truly appreciate your time.

---

