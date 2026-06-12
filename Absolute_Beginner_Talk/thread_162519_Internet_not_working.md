---
title: "Internet not working"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by shmida on 2006-04-19
I just installed ubuntu (dual boot) and my DLINK DSL-504T adsl modem (ethernet) is configured and ready to go but i can't go on any sites or anything. Net working fine with XP please help

---

### Post by mips on 2006-04-19
You should really try and provide more information on your problem.

All we know is you have a modem, nothing more.

Now I have to sit and type out the following questions in order to determine the nature of your problem:

What type of modem, dial-up, adsl, cable, sattelite ?
What type of connection does it have, serial, Ethernet, USB ?
What make & model is the modem ?

The response you get is directly proportional to how well you ask your question, keep this in mind when seeking help ;)

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by shmida on 2006-04-19
Sorry, forgot to add that in.... first cup of ubuntu

---

### Post by mips on 2006-04-19
1. Please disable IPv6 and reboot:
[B]sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a[/B]
2. Please post output of **ifconfig eth0**   (Depending on interface number)
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of [COLOR="Red"]ms-windows[/COLOR] **ipconfig /all** command here
8. Who is your ISP, link to website please ?

---

### Post by shmida on 2006-04-19
[QUOTE=mips]1. Please disable IPv6 and reboot:
[B]sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a[/B]
2. Please post output of **ifconfig eth0**   (Depending on interface number)
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of [COLOR="Red"]ms-windows[/COLOR] **ipconfig /all** command here
8. Who is your ISP, link to website please ?[/QUOTE]

2.Link encap:Ethernet  HWaddr 00:0F:EA:78:F2:D5
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:eaff:fe78:f2d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2220 (2.1 KiB)  TX bytes:2015 (1.9 KiB)
          Interrupt:19 Base address:0xe800

3. 0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

4.Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0	10.1.1.1        0.0.0.0         UG    0      0        0 eth0


5. nameserver 10.1.1.1

6. # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

7. 
Windows IP Configuration

        Host Name . . . . . . . . . . . . : MOLONEY
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900 PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-0F-EA-78-F2-D5
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.1.1.2
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . : 10.1.1.1
        DHCP Server . . . . . . . . . . . : 10.1.1.1
        DNS Servers . . . . . . . . . . . : 10.1.1.1
        Lease Obtained. . . . . . . . . . : Wednesday, April 19, 2006 10:40:14 P
M
        Lease Expires . . . . . . . . . . : Wednesday, April 19, 2006 11:40:14 P
M


8. .netcall [http://www.netcall.com.au/](http://www.netcall.com.au/)

---

### Post by mips on 2006-04-21
Can you ping the following IP addresses:
10.1.1.1
212.58.224.36
198.133.219.25
202.63.43.134

Can you ping the following host names:
[www.bbc.com](www.bbc.com)
[www.cisco.com](www.cisco.com)
[www.netcall.com.au](www.netcall.com.au)

Ping works from the command line/terminal and you simply type the command ping followed by ip addres or host name.

If you can ping via IP address and not host name then edit your resolv.conf file. Remove the existing nameserver address and add two new ones depending on your location:
Queensland
nameserver 202.63.43.130
nameserver 202.63.39.130

NSW
nameserver 202.63.43.130
nameserver 202.63.39.130

Victoria
nameserver 202.63.39.130
nameserver 202.63.43.130

SA/WA/NT
nameserver 202.63.39.130
nameserver 202.63.43.130

---

