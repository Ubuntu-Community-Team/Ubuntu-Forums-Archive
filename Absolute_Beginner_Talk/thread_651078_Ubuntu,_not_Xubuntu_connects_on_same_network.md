---
title: "Ubuntu, not Xubuntu connects on same network"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by speedinbil on 2007-12-27
I have changed all the settings in xubuntu to the same as ubuntu as I can on the network connection.  Xubuntu still will not connect.  the only thing I can see that isn't the same not in the network connection is the mask, would it helped if I changed that?  Mepis can connect just fine to the internet as well installed or on a live cd with the same computer and physical setup. Are there settings more detailed I need to change or...?  Please help!
Thanks
Speedinbil

---

### Post by jken146 on 2007-12-27
Yeah, change the mask so that it's the same as in the working connection settings.

---

### Post by speedinbil on 2007-12-27
I have been searching on how to change the mask, how do I change it?
Speedinbil

---

### Post by p_quarles on 2007-12-27
You would have to edit the following file:
```
/etc/network/interfaces
```
If you could post the contents of this file, I or someone else can tell you precisely what to change.

---

### Post by speedinbil on 2007-12-27
I found something to change the netmask, but it says that SIOCSIFFLAGS: Device or resource busy
the command was sudo ifconfig eth0 192.168.2.1 netmask 255.255.255.0 up
so I am not sure why that said it was busy, could i have typed in the wrong eth address?  
how do I make sure eth0 is what I am suppose to use?
or should I scratch that way and just edit the file?
I know where to find the file, but how do I edit it?  I was going to try to copy the folder from my computer with ubuntu the network folder and paste it into the xubuntu etc dir but it wouldn't let me do that either, I am not sure how to log in as superuser in the file browser.
here are the file contents of /etc/network/interfaces leaving out the notes

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0
 what do I need to change it to?
Thanks
Speedinbil

---

### Post by p_quarles on 2007-12-27
Okay, looks like you're on DHCP. Are you certain the "auto eth0" line comes *after* the line saying "iface eth0 inet dhcp"? If so, that would seem to be the problem. 

Anyway, what's the result of this:
```
ifconfig -a
```
That will list the current settings for your network devices.

---

### Post by speedinbil on 2007-12-27
results 
@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:46:E6:E8:41  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153600 (150.0 KB)  TX bytes:153600 (150.0 KB)

contents of file

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp

auto eth0

these are the file contents of network on the computer that has a working connection
auto lo
iface lo inet loopback


iface eth0 inet dhcp





auto eth0

and those are the results of the addresses in the router webface

 Firmware Version	9.01.07
   Boot Version	0.01
   Hardware	01
  
	  	
LAN Settings
   LAN/WLAN MAC	00-17-3F-5F-4A-FF/
   IP address	192.168.2.1
   Subnet mask	255.255.255.0
   DHCP Server	Enabled


Internet Settings
   WAN MAC address	00-17-3F-5F-4B-00
   Connection Type	Dynamic
   Subnet mask	255.255.255.0
   Wan IP	192.168.0.5
   Default gateway	192.168.0.1
   DNS Address	192.168.0.1
	
and those are the results of the addresses in the router webface

Thanks
Speedinbil

---

### Post by p_quarles on 2007-12-27
Well, I can't be sure that this will fix it, but try it anyway. Edit the interfaces file by using this command:
```
gksudo gedit /etc/network/interfaces
```
And move the line that says "auto eth0" above the line that's currently before it. 

Now, restart the networking system to test it:
```
sudo /etc/init.d/networking restart
```
Any difference?

---

### Post by speedinbil on 2007-12-27
I couldn't save the changes for some reason, but these are the results of the restart


william@ubuntu:~$ gksudo gedit /etc/network/interfaces
william@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 13471
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:46:e6:e8:41
Sending on   LPF/eth0/00:13:46:e6:e8:41
Sending on   Socket/fallback
SIOCSIFFLAGS: Device or resource busy
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:13:46:e6:e8:41
Sending on   LPF/eth0/00:13:46:e6:e8:41
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

---

### Post by p_quarles on 2007-12-27
You couldn't save the changes? That's odd. Anyway, try using the command line text editor to change the file:
```
sudo nano /etc/network/interfaces
```
Then run the restart command again.

That said, based on the output that you got running the command, it's starting to look like an ipv6 issue. If editing the interfaces file doesn't work, I'll find a guide to disabling ipv6.

---

### Post by speedinbil on 2007-12-27
still no luck.  I am not sure why it works so well in ubuntu and not in Xubuntu.  what could be so different, it didnt take this much time or configuring, or even why mepis works.  Could it really be ipv6 if i cant even pull up the screen for my router?  I am just a novice but trying anything I can think or learn about.  could it still be the mask, and would it need to be changed, if so how, and why does it say the system is busy?
Thanks,
Speedinbil

---

### Post by speedinbil on 2007-12-30
I would just like to thank you both for your help.  I finally got it working.  It must have been something we did, I wish I knew what exactly.  I re ran the pppoe program and it worked this time when it didn't work before.
  
Thanks!

Speedinbil

---

