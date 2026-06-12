---
title: "Where to Ask about Ubuntu Server"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-09-22
I work at a small town library computer center where we want to teach an html class using a donated computer with Ubuntu 6.06 Server. There are about 20 XPs on our little network.

I've installed it, and gone through the "perfect setup ubuntu 6.06" on sourceforge.net. No errors came up anywhere, but I can't "ping" the Ubuntu box, even if I ping its IP address, and I can't anything else from the Ubuntu box. 

It seems like I should be able to do that before I start on anything else. Can anyone direct me to a starting point?

Gary

---

### Post by crokett on 2006-09-22
You installed Ubuntu?  Are you using DHCP or static IPs?  If DHCP does the DHCP server show a reservation for the Ubuntu server?   

what does ```
sudo ifconfig 
``` show for IP address information? 

Ubuntu server installs the IPTables firewall by default.  This may be causing your problem, though I think there are also no rules by default so nothing should be blocked.

---

### Post by Gary Nored on 2006-09-22
Yes. I installed Ubuntu Server 6.06.

ifconfig looks like this: 

locknet70@lcnet70:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:06:5B:1D:A0:60
          inet addr:10.100.15.122  Bcast:10.100.15.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe1d:a060/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23410 errors:0 dropped:0 overruns:1 frame:0
          TX packets:8431 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:13678294 (13.0 MiB)  TX bytes:913518 (892.1 KiB)
          Interrupt:185 Base address:0x8c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

-----------------

I edited /etc/network/interfaces to look like this: 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
  address 10.100.15.55
  netmask 255.255.255.0
  network 10.100.15.0
  broadcast 10.100.15.255
  gateway 10.100.15.1
  dns-nameserver 192.168.1.254

--------
the hosts file looks like this:

127.0.0.1	localhost
10.100.15.55	lcnet70

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I don't know how to interpret this. DHCP? I know what it means, I can get on the internet, so I know it's being used somehow, but I don't know how to answer your questions. 

Gary

---

### Post by crokett on 2006-09-22
> **Gary Nored said:**
> Yes. I installed Ubuntu Server 6.06.

I don't know how to interpret this. DHCP? I know what it means, I can get on the internet, so I know it's being used somehow, but I don't know how to answer your questions. 

Gary

Ok.  If you can get on the internet from your Ubuntu server then your network interface is active and working.  DHCP means that if you have a DHCP server active your computers will be assigned IP addresses automatically.  

Your ip address for that machine is currently 10.100.15.122  Is this what you were pinging from Windows? We know this server can see the default gateway since your internet access works. So... what IP addresses are assigned to the Windows machines? What does ipconfig /all show? 


Your ifconfig file for eth0 should have a DHCP setting or an IP Address but not both (as you have currently in the file)

---

### Post by Gary Nored on 2006-09-22
You're right -- I checked my cmd window history and discovered I was pinging .22 instead of .122. 

How do I configure this machine to have one static ip address?

btw -- home for the weekend. I probably won't get back to you until Monday. 

Gary

---

### Post by crokett on 2006-09-22
> **Gary Nored said:**
> You're right -- I checked my cmd window history and discovered I was pinging .22 instead of .122. 


Heh. Its always the simple stuff. ;) I still forget that sometimes.

[QUOTE=Gary Nored]
How do I configure this machine to have one static ip address?
[/QUOTE]

Preferred method is to give MAC address of the adapter to your admin and add a reservation on your DHCP server.  That way it stays DHCP but always gets the same address.  Among other things you still automatically get your DNS, default gateway, etc assigned.  So if those ever change you don't break the Ubuntu box.  

Your MAC address for this machine is: 00:06:5B:1D:A0:60 <-- this is the Ethernet HWAddr that ifconfig displays.  

Otherwise edit /etc/network/interfaces and change 'dhcp' to static then set the ip address to what you want.  or from the Desktop GUI there is an option to configure that way.  either way you configure it you will have to know what to set your gateway and dns servers to.

---

### Post by jamesr on 2006-09-22
Hi,

Are you connected to another network or totally independant. Is your configuration 
server===hub===20 PCS
or
server===router==20 PCs
           !!
         Internet

---

