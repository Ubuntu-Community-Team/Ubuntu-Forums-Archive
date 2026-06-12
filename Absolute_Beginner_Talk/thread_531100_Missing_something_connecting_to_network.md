---
title: "Missing something connecting to network"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by dodgy_devil on 2007-08-21
Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
About to throw my computer out the window...........
I have dual booted with windows xp, on windows xp my network connects perfectly, so there is nothing wrong with the network cart or the cable, I have also read through almost all the network related posts and could still not find a solution.
Cant seem to connect to the router, can't even ping any of the other computers on the network. It just seems if their is no connection. I have configured the ethernet connection to a static IP 192.168.0.59 subnet mask 255.255.255.0  i have also set the default gateway the same as all the other computers on the network. (No IP conflicks)Our DNS is the same as the gateway
I've also shutdown my pc and unplugged the network cable as well as the power before booting into Ubuntu, but still no connection.
Am i missing something. The network adapters are both activated as well. Is there still another plase i have to activate the network. On my previous installation it worked perfectly. But i had to format


Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I get the following if i run ifconfig -a

jake@Dodgy:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1A:92:16:A0:13  
          inet addr:192.168.0.69  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe16:a013/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247781 (241.9 KiB)  TX bytes:4230 (4.1 KiB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:1A:92:16:B4:FB  
          inet addr:192.168.0.59  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6427 (6.2 KiB)  TX bytes:6427 (6.2 KiB)

ra1       Link encap:Ethernet  HWaddr 00:08:A1:A9:AA:21  
          inet addr:192.168.0.234  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fea9:aa21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1539509 (1.4 MiB)  TX bytes:0 (0.0 b)
          Interrupt:23

---

### Post by Austin_KW on 2007-08-21
First question, whay are you using static ip addresses, dhcp is so much easier and will configure everything for you. But that is your choice.

What is the output of the command "route -n"

eth0 and eth1 are both up, are they both cabled to the router? if not take down the interface that is not cabled, It looks like there is no cable on eth1 (sudo ifconfig eth1 down ) or you may try to route over the uncabled interface.

What is ra1, some sort of rt2500/rt61 wireless? Why are you using ethernet if you also have wireless? If this connection is not configured correctly you may also want to temporarily take it down to get eth0 to work (sudo ifconfig ra1 down)

---

### Post by wirelessmonkey on 2007-08-21
Do you have DNS configured properly?

---

### Post by Austin_KW on 2007-08-21
> **wirelessmonkey said:**
> Do you have DNS configured properly?

That would not stop pinging of local network.

---

### Post by wirelessmonkey on 2007-08-21
Um, yeah, I managed to not read that entire line.  Apologies. 

Can you ping your router?  

Try
sudo ifconfig eth0 down
sudo ifconfig eth0 up
dmesg |  tail

and post the output.

---

### Post by dodgy_devil on 2007-08-22
I am still not able to connect, i have tried to ping one of the other computers on the network:
Here is the data you asked for

jake@Dodgy:~$ sudo ifconfig eth0 down
jake@Dodgy:~$ sudo ifconfig eth0 up
jake@Dodgy:~$ dmesg | tail
[ 1106.655292] skge eth0: enabling interface
[ 1106.660986] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1182.778617] sky2 eth1: disabling interface
[ 1195.208691] sky2 eth1: enabling interface
[ 1195.211084] sky2 eth1: ram buffer 0K
[ 1196.910557] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control both
[ 1206.063854] eth1: no IPv6 routers present
[ 1581.729768] skge eth0: disabling interface
[ 1600.467672] skge eth0: enabling interface
[ 1600.473353] ADDRCONF(NETDEV_UP): eth0: link is not ready
jake@Dodgy:~$

---

### Post by wirelessmonkey on 2007-08-22
Ok, so in looking at this info, I noticed that you are using the sky2/skge driver for your ethernet adapter.  I know historically that this driver has had a number of problems, but most were fixed in recent kernels.  Are you running Ubuntu Feisty?  
Please post the output of:
#  uname -r

and 

# lshw | grep network

---

### Post by wirelessmonkey on 2007-08-22
I can't believe I missed this... sorry!  When you showed your DNS configuration, it was setup incorrectly.   edit your /etc/resolv.conf  and comment out the addresses listed.

on a clean line, enter the ip of your router, 192.168.0.59, then sudo /etc/init.d/networking restart.

Let me know if that works!

---

### Post by schorsch on 2007-08-22
Well, you have three interfaces in your system: 2 are wired (eth0, eth1) and 1 seems to be wireless (ra1). All of them seem to have a static IP.
eth0: 192.168.0.69
eth1: 192.168.0.59
ra1:   192.168.0.234
The output of the dmesg command you posted says that eth0 has no link whereas eth1 has a link. Have you already done what Austin-KW suggested yesterday? Please post the output of the following command:
```
netstat -nr
```
Perhaps you are routing over eth0 which seems to be uncabled ...  Just forget about the wireless for the moment although it is weird to have three interfaces up and running at home unless you use the system as a firewall or a router .....

---

