---
title: "Can't get network card to work"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-05-10
it was working initially, then I wanted to give myself a static ip to allow the router ports to be setup.  Once I said allow for manual configuration my network card is no longer able to connect to the router, and I cannot get that Network Manager applet back.

Any help would be appreciated.

---

### Post by [S|G] on 2007-05-10
You can configure your network manually if you edit your interfaces file:
```
sudo gedit /etc/network/interfaces
```
There you'll find the definitions for your network cards. An example for a fixed-ip adress would be something like this:
```

auto eth0
iface eth0 inet static
address 192.168.131.169
netmask 255.255.254.0
gateway 192.168.130.222

```
After you configure that you should restart your networking:
```
/etc/init.d/networking restart
```
Of course, getting your applet back would help a lot, since it's way more intuitive... I'm not all familiar with the gnome interface, so I hope this might help for now :)

---

### Post by Najand on 2007-05-10
try ifconfig and send its output to us here!

---

### Post by chris.olsen on 2007-05-11
it is good now, after running the restart.

Thanks

I should add that the icon in the top left is there, but I am only given the option for "Manual Configuration".  Being able to see the wireless networks strengths is now gone.

---

### Post by chris.olsen on 2007-05-12
both my wireless and lan networks are down again.  I did the restart, seeing as it worked last time, but got nothing.  I can't ping the router either, and of course the other computers on my network do work fine so it isn't a networking issue.

help

---

### Post by [S|G] on 2007-05-12
Type this and paste the output here:
```
ifconfig
```

---

### Post by chris.olsen on 2007-05-12
chris@ubuntu:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 4431
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:a8:11:3a
Sending on   LPF/eth1/00:13:02:a8:11:3a
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:a8:11:3a
Sending on   LPF/eth1/00:13:02:a8:11:3a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.148 -- renewal in 42345 seconds.
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

============================

chris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:1E:C6:32  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:13:02:A8:11:3A  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fea8:113a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:217 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2267 (2.2 KiB)  TX bytes:5317 (5.1 KiB)
          Interrupt:16 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23784 (23.2 KiB)  TX bytes:23784 (23.2 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.159.1  Bcast:192.168.159.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


============================
chris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"23Below"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:ED:22:CE   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-46 dBm  Noise level=-47 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:217   Missed beacon:0

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.


Thanks for the help

---

### Post by Kobalt on 2007-05-12
If you edit the /etc/network/interfaces file manually then you cannot use Network-Manager : it needs to be the only one managing network settings otherwise it conflicts and doesn't work anymore. If so, you need to remove it with Synaptic and use the good old network-monitor applet : right-click on your panel and select Add to the panel. Scroll down to system and tools and there it is.

---

### Post by chris.olsen on 2007-05-12
My cards are now working again (this is a little frustrating).

Kobalt: when you say "If so, you need to remove it with Synaptic " are you referring to removing the network manager applet, then re-installing it?

Currently the Network Manager Applet is not available in the System Tools section after clicking Add to Panel

---

### Post by chris.olsen on 2007-05-12
BTW: The network manager is there, I just have the Manual Configuration option available, and that is the same after re-installing it.

I did get this error message when re-installing the network-manager, although it is not very descriptive

--> The NetworkManager applet could not find some required resources.  It cannot continue.

---

### Post by [S|G] on 2007-05-12
You can try reinstalling it like this:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```

---

### Post by chris.olsen on 2007-05-12
I have already uninstalled them, then re-installed them.  I did run your re-install script anyway, but nothing has changed. I still have the network icon in the top corner, but the only option that is given is Manual COnfiguration.

---

### Post by Kobalt on 2007-05-13
I meant completely removing it but not installing it back (since it could be conflicting). 

PS: Network-Manager isn't in the *Add to the panel* menu, you need to start it with the command *nm-applet*.

---

### Post by chris.olsen on 2007-05-13
everything was working fine, until I set up a static IP address by clicking on manual configuration.

After that it often doesn't connect on startup, take say this morning.  running the network restart seems to fix it though.

I would like to keep the networkmanager applet, because it allow detecting broadcasted wireless networks much easier, unless there is a tool out there, which I am sure there is, that will still allow for this.

I will remove it, and see if it improves things.

Thanks

---

### Post by chris.olsen on 2007-05-13
I removed it, but still had problems on start-up and had to run the network restart command.

---

### Post by chris.olsen on 2007-05-13
after clearing the /etc/network/interfaces file that applet is now managing things properly.  I still would like to be able to setup a static IP without losing the applet, but this does allow me to more easily find public networks.

---

