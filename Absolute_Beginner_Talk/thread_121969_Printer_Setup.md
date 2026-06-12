---
title: "Printer Setup"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-26
Hi there I have followed the below steps to configure my network printer but no use 

1. Go into the printers control panel and choose Printer > Add Printer.
2. Select Network Printer and use the listbox to choose HP JetDirect.
3. In the Host box type the IP address of your printer.(with Port 9100 default)
4. Click Forward.

It seems printing always so what is the problem? Is there a possible network problem?

Thx

---

### Post by bscbrit on 2006-01-26
From the command line, can you ping your printer?

Try the following

ping <PRINTER_IP_ADDRESS> -c5

This will let you know whether the network side of things is working.  Let me know the results, please.

---

### Post by utab on 2006-01-26
Result I guess PROBLEM

PING 10.33.172.24 (10.33.172.24) 56(84) bytes of data.
From 10.33.172.140 icmp_seq=1 Destination Host Unreachable
From 10.33.172.140 icmp_seq=2 Destination Host Unreachable
From 10.33.172.140 icmp_seq=3 Destination Host Unreachable
From 10.33.172.140 icmp_seq=4 Destination Host Unreachable
From 10.33.172.140 icmp_seq=5 Destination Host Unreachable

--- 10.33.172.24 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4008ms
, pipe 3

---

### Post by bscbrit on 2006-01-26
Yes, its a network problem. What is the output from the following command:

ifconfig

?

---

### Post by utab on 2006-01-26
[QUOTE=bscbrit]Yes, its a network problem. What is the output from the following command:

ifconfig

?[/QUOTE]

eth0      Link encap:Ethernet  HWaddr 00:12:3F:1A:E8:C1
          inet addr:10.33.172.140  Bcast:10.33.175.255  Mask:255.255.252.0
          inet6 addr: fe80::212:3fff:fe1a:e8c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12644316 (12.0 MiB)  TX bytes:1405193 (1.3 MiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:462706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39348824 (37.5 MiB)  TX bytes:39348824 (37.5 MiB)

---

### Post by bscbrit on 2006-01-26
Ok, lets do this in stages.  First, confirm that your network card is working:

ping localhost -c5
and
ping 10.33.172.140 -c5

You should get a good response from this, if not your card is not working correctly but the indications from ifconfig suggest that this is not the problem.

Check the cable(s) between the computer and the printer.  If you have a hub/router you need 2 x standard cables.  If you have a direct connection from the ethernet port on the computer to the ethernet port on the printer you should use 1 x cross-over cable (null-cable).  Assuming that your cables are correctly wired and functioning, we must next check the printer.

What model of HP printer have you got? The method of checking the printer's IP address will probably vary from model to model (at least slightly).  I use a HP4050 and can use the printer menu to check the IP address that it is set to use.  Please confirm that you have the setting that you think that you should have.

---

### Post by utab on 2006-01-26
the first
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.037 ms64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.028 ms64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=3 ttl=64 time=0.029 ms64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=4 ttl=64 time=0.027 ms64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=5 ttl=64 time=0.027 ms
--- localhost.localdomain ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.027/0.029/0.037/0.007 ms

the second

PING 10.33.172.140 (10.33.172.140) 56(84) bytes of data.

--- 10.33.172.140 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3998ms

I have at work one HP LaserJet 1320 and HP LaserJet 4000N but 4000 is connected to a Win2000 computer and 1320 is directly connected to the network. So I do not know whether it can help.

The configuration for 4000N is the one recommended(postscripts) in the list of printers I just tried this because I got the IP address of this computer only.(since the other one is directly connected to the network I could not figure that out.)

Thx.

---

### Post by utab on 2006-01-26
Now I am at home so things may change maybe I do not know

thx.

---

### Post by bscbrit on 2006-01-26
Which printer are you trying to set up?  You cannot use jetDirect if the printer is connected to the parallel port of the computer.

---

### Post by utab on 2006-01-26
Oops, Tried the one connected to the computer. The other one is directly connected to the network plug.

SO?

thx.

---

### Post by bscbrit on 2006-01-27
utab, I think I understand what you mean but surely both printers are connected to the computer?.  I think that one is connected by the parallel port and the second by an ethernet connection.  

Please tell me :

Which printer are you trying to get working? - lets do one at a time!

How is it connected to the computer?

Does the ethernet connection (if used) go via a hub/router or is it directly connected between the computer and the printer?

What make and model of printer is it?

---

