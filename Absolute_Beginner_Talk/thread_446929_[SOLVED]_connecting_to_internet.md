---
title: "[SOLVED] connecting to internet"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by raequin on 2007-05-17
My problem: A new install can not connect to the internet.


My laptop has had Ubuntu for a few months.  I've use Network Settings to connect to the internet in a few places with it.  I just recently added a dual boot to the desktop in my office at a university.  The computer can connect to the internet when running Windows but not Ubuntu.

From here on out we're treading on ground that's unfamiliar to me.  The school gave my office computer a static IP.  I copied that down, as well as the subnet mask, gateway address, and DNS server.  Entering all of this information into Network Settings in Ubuntu does not help.

I asked an employee of the school and he said, "It could be a number of different things. Is the network card recognized and enabled in linux? Is there more than one network card in the system?  I suggest you go to your linux distribution website and see if they have documentation on configuring and enabling a network interface card."

So, any help?  I would surely appreciate it as I would like to get to use Ubuntu for work at school.

---

### Post by blazercist on 2007-05-17
on the linux pc: open a terminal and type sudo ifconfig -a
paste the output here.

Also, lets do a little troubleshooting, can you ping an external ip address from the terminal?

Try pinging google.com by its IP address not its hostname. IF this is successful This will tell you if its a DNS problem.

Also, can you try pinging another computer on your network?  Tell us what happens when you try these things.

---

### Post by raequin on 2007-05-22
I was out of office, that's why it took me so long to reply.  I believe the pasted data, below, has all the info you mentioned.

eth0      Link encap:Ethernet  HWaddr 00:50:BA:54:11:BB  
          inet addr:128.61.140.157  Bcast:128.61.140.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe54:11bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7268444 (6.9 MiB)  TX bytes:183609 (179.3 KiB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


$ ping 216.239.57.99 (google)
PING 216.239.57.99 (216.239.57.99) 56(84) bytes of data.

--- 216.239.57.99 ping statistics ---
417 packets transmitted, 0 received, 100% packet loss, time 416066ms


$ ping 128.61.140.152 (computer on network)
PING 128.61.140.152 (128.61.140.152) 56(84) bytes of data.
64 bytes from 128.61.140.152: icmp_seq=1 ttl=128 time=1.33 ms
64 bytes from 128.61.140.152: icmp_seq=2 ttl=128 time=0.287 ms
64 bytes from 128.61.140.152: icmp_seq=3 ttl=128 time=0.469 ms
64 bytes from 128.61.140.152: icmp_seq=4 ttl=128 time=0.196 ms
64 bytes from 128.61.140.152: icmp_seq=5 ttl=128 time=0.397 ms
64 bytes from 128.61.140.152: icmp_seq=6 ttl=128 time=0.568 ms
64 bytes from 128.61.140.152: icmp_seq=7 ttl=128 time=0.299 ms
64 bytes from 128.61.140.152: icmp_seq=8 ttl=128 time=0.477 ms
64 bytes from 128.61.140.152: icmp_seq=9 ttl=128 time=0.240 ms
64 bytes from 128.61.140.152: icmp_seq=10 ttl=128 time=0.392 ms
64 bytes from 128.61.140.152: icmp_seq=11 ttl=128 time=0.579 ms

--- 128.61.140.152 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10000ms
rtt min/avg/max/mdev = 0.196/0.476/1.335/0.297 ms

---

### Post by Austin_KW on 2007-05-22
Have you set your default route (or gateway)
what is the output of the command "route"

and can you ping your gateway.

---

### Post by raequin on 2007-05-22
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.61.140.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         router.me.gatec 0.0.0.0         UG    0      0        0 eth0



$ ping 128.61.140.1  (gateway)
PING 128.61.140.1 (128.61.140.1) 56(84) bytes of data.
64 bytes from 128.61.140.1: icmp_seq=1 ttl=255 time=0.526 ms
64 bytes from 128.61.140.1: icmp_seq=2 ttl=255 time=0.537 ms
64 bytes from 128.61.140.1: icmp_seq=3 ttl=255 time=0.539 ms
64 bytes from 128.61.140.1: icmp_seq=4 ttl=255 time=0.997 ms
64 bytes from 128.61.140.1: icmp_seq=5 ttl=255 time=0.539 ms

--- 128.61.140.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.526/0.627/0.997/0.186 ms

---

### Post by raequin on 2007-05-22
resolved - in Network Settings, I unchecked "Automatic service discovery."  Now the connection works.  Thanks for your help.

---

