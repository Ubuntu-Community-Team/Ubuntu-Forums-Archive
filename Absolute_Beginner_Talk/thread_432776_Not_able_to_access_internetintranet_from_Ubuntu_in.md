---
title: "Not able to access internet/intranet from Ubuntu installed on VMware on Windows XP"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-05-04
Hi,
I have installed Ubuntu 7.04 on VMWare Workstation 5.5.1 on Windows XP SP2. Ubuntu works fine inside virtual computer. The only problem is I can't access to network or internet.

I have set settings at:
1. System | Administration | Network | Wired connection | Properties
2. Static IP address - IP address, subnet mask, gateway address
3. DNS tab: IP of DNS Server.

Pinging local network computer I get error:
connect: Network is unreachable

Executing ifconfig I get the following info:
```

eth0      Link encap:Ethernet  HWaddr 00:0C:29:4A:79:A7
          inet6 addr: fe80::20c:29ff:fe4a:79a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:90223 (88.1 KiB)  TX bytes:42310 (41.3 KiB)
          Interrupt:18 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4708 (4.5 KiB)  TX bytes:4708 (4.5 KiB)
```

Any idea what is wrong? I can connect from host Windows XP to network and I can also successfully ping remote computer. So Windows (host) network is working properly, but virtual Ubuntu is not? Any idea?

Thanks,
Abcuser

---

### Post by Anicka on 2007-05-04
Try the different options in the VM -> Settings menu (bridge network, NAT...) I use NAT because it works for me when I want to access the internet and so on.

---

### Post by waynep on 2007-05-04
Check the Network Manager Applet in the upper right hand corner.  Click on it and see if the "Wired Connection" radio button it selected. 

wayne

---

### Post by abcuser on 2007-05-08
> **waynep said:**
> Check the Network Manager Applet in the upper right hand corner.  Click on it and see if the "Wired Connection" radio button it selected. 

wayne
Check box in Wired Connection is checked.

---

### Post by abcuser on 2007-05-08
> **Anicka said:**
> Try the different options in the VM -> Settings menu (bridge network, NAT...) I use NAT because it works for me when I want to access the internet and so on.
I have tried using NAT, but executing ping command I got "Destination Host Unreachable" error.

---

### Post by justleen on 2007-05-08
have you tried bridged networking with DHCP (on your vm)? how did that work?

---

### Post by abcuser on 2007-05-09
Bridged networking with DHCP is not working. It is obvious because there must exist DHCP server to dynamically assign IP address.

---

### Post by oilchangeguy on 2007-05-09
you should be able to use NAT. that enables the virtual machine to use the host machines internet connection.

---

### Post by saip106 on 2007-06-12
I had a similar problem and I changed my settings as follows and restarted the Virtual Machine and internet is working fine now.

[http://img161.imageshack.us/my.php?image=croppercapture18qr8.png]("http://img161.imageshack.us/my.php?image=croppercapture18qr8.png")

[IMG]http://img161.imageshack.us/my.php?image=croppercapture18qr8.png[/IMG]

Hope this helps...

Sai

---

### Post by n.g.machado on 2007-06-22
Hi, I have a question.
I installed VMServer 1.0.2 on windows vista, and in a new VMachine I run KUBUNTU from the CD, in that moment I setup the NIC interface in mode NAT, then in the Kubuntu sesion I can connect to internet.

So I decided to install Kubuntu on that VM, and after that I can't connect to internet.

When I look to the NIC on kubuntu i have a DHCP connection that assigned this ip:
192.168.17.128, and a gateway in 192.168.17.2

on the windows:
I have a virtual network card with the IP 192.168.17.1

Today I will try again with the Live CD version of kubuntu.

i have to use NAT because I have a USB ADSL modem, I'm in Argentina, just in case any of you be near me.

Any idea will be appreciated

Best Regard Nicolas

---

