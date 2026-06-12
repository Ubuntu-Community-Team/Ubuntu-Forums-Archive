---
title: "Almost have my new DSL connection working, need a little help"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-07-21
I had my cable modem connection working but decided to switch to DSL because I am frustrated with my cable provider. (Comcast) I ended up with SBC-Yahoo DSL,
that uses a 2wire brand DSL modem with built in wireless router. 

  Okay so now I can connect to the DSL after many hours of playing around. I ended up downloading a wireless manager from synaptic ( wireless assistant ).
I can connect using the wireless manager but each time I reboot or log-off I loose my connection and must start up the wireless assistant to connect. 
It seems that all my settings are correct. Anyway I am enclosing the terminal stuff from wlassistant plus ifconfig and iwconfig. I have no idea what the wlassistant is finding when it first starts and finds a bad device? Perhaps the built in network card that I am not using?

Anyway here is the goods


rich@ubuntu:~$ sudo wlassistant
Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhcpcd
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): eth0
Permissions checked.
ifconfig_status: /sbin/ifconfig eth0
ifup: /sbin/ifconfig eth0 up
scan: /sbin/iwlist eth0 scan
Networks found: 1
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcpc/dhcpcd-eth0.info
Gateway address: xxx.xxx.x.xxx
Checking for active connection.
Checking for active connection.
Checking for active connection.
Checking for active connection.
kill_dhcp: /sbin/dhcpcd -k eth0
==>stderr: ****  /sbin/dhcpcd-bin: not running
ifup: /sbin/ifconfig eth0 up
iwconfig_set: /sbin/iwconfig eth0 mode managed channel 6 key open xxxxxxxxxx essid 2WIRE443
iwconfig_ap: /sbin/iwconfig eth0 ap 00:18:3F:20:BB:01
ifconfig_dhcp: /sbin/dhcpcd -nd eth0
Internet now accessible.


rich@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:"2WIRE443"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:20:BB:01
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-60 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

rich@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:17:74:43:C6
          inet addr:xxx.xxx.x.xxx  Bcast:xxx.xxx.x.xxx  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe74:43c6/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15709 (15.3 KiB)  TX bytes:15990 (15.6 KiB)
          Interrupt:177 Memory:fdcfe000-fdd00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:920 (920.0 b)  TX bytes:920 (920.0 b)



Any help would be appreciated

Peace
Rich

---

### Post by hajk on 2006-07-21
May be you're making it unnecessarily difficult, what with wireless assistant and all... There are two issues that you must address: (1) getting your local network going with the router as DHCP server; and (2) getting the DSL modem to connect to your ISP.

(1) Assuming that your wireless card/driver is all working OK, open the System -> Administration -> Networking menu item, and there should be a wireless interface present, like wlan0 or ath0 (name depends on the chipset in your wireless device). Highlight the interface, make sure it is deactivated, and hit Properties: enable the interface, choose the essid, set the wep key and select DHCP, then accept these settings. Now activate the interface, and you should then be able to connect to the router. You need do this only once.

(1.5) It may be necessary for you to open the router for new connections first -- see the router manual. On many SpeedTouch routers/modems you should press and hold a button on the front panel 2-3 seconds, after which new connections are accepted during 1 minute. You need do this only once, as the router/modem remembers the MAC address of your wireless device.

(2) Configuring the modem: you must now log in to it in your browser -- look in the router manual for the default IP address (usually something like 192.168.1.254), and configure it. If you don't have a wireless connection to the router, then you may alternatively set up a wired Ethernet connection first, more or less as in item (1). Your ISP should have given you the details of the connection, or you could phone them for the details. 

Good luck!

---

### Post by ChrisDerson on 2006-07-21
As far as I can tell the first block of error messages you get ('BadDevice') refer to your loopback interface (lo) - every TCP-IP aware machine has a loopback device (IP address 127.0.0.1) which is used for testing, and as a fallback if an application absolutely must have a working TCP-IP connection.  The loopback intergace runs even if no network cards etc are installed.
My first guess is that the eth0 interface (your wireless network card) is not configured to auto-start.  Please post the contents of your /etc/network/interfaces file, I'd take the time to blank out your ESSID and wireless-key.
I'm hoping it'll be a quick fix from there.

---

### Post by ChrisDerson on 2006-07-21
(1) The interface is eth0 (a bit unusual - it is usually wlan0).  It *must* have the ESSID and wirless-key set (they crop up in the logs) so don't need to be set again.
(1.5) No, you probably don't need to mess around with the router, since your network connection works after you enable it.
(2) No, you don't need to configure the 'modem' - the ifconfig output shows you have an IPv4 address (probably 192.168.1.10 or similar, and a broadcast address (probably 192.168.1.255) and a netmask.  ifconfig *will not* list these if they are not set.  Also, since you have a 'working' connection after you run the wlassistant command (I assume you test with a browser) we can safely assume that everything else is working Ok.  Your problem is getting the eth0 interface to auto start.  It is *not* a problem with the eth0 configuration.

---

### Post by Rich3077 on 2006-07-21
Thanks for the replys. I think you guys are onto something about the network interface (eth0) not starting automatically. Here is the contents of my 
/etc/network/interfaces file

### etherconf DEBCONF AREA. DO NOT EDIT THIS AREA OR INSERT TEXT BEFORE IT.
auto lo

iface lo inet loopback

iface eth0 inet dhcp
        hostname ubuntu
        wireless-essid xxxxxxxx
        wireless-key xxxxxxxxxx


### END OF DEBCONF AREA.  PLACE YOUR EDITS BELOW; THEY WILL BE PRESERVED.


iface dsl-provider inet ppp
provider dsl-provider





auto eth0

Thanks
Rich

---

### Post by Rich3077 on 2006-07-21
I still need help with this issue.. I will post more about it tomorrow as I am rather intoxicated right now. I just got out of a hearing in which I was charging my union officials with corruption.. beleive it or not I think it went well. 
errrr  I will check up on this thread tomorrow.. untill then I must deal with Win XP.

---

### Post by lowey23 on 2006-07-21
Don't worry about being a little intoxicated. Computers know when you have been drinking and they automatically break something for you to fix tomorrow. :-k

---

### Post by ChrisDerson on 2006-07-26
Sorry about the delay - much power related silliness at work eat all my time :(
How odd.  AFAIK the 'auto eth0' line should start your wireless NIC as soon as the system detects that it is there (e.g at boot).  What sort of wireless device is it, and how is it attached to your PC?
Also, what do you get if you run ifconfig eth0 and iwconfig eth0 before you run wlassistant?

---

### Post by Rich3077 on 2006-07-27
> **ChrisDerson said:**
> What sort of wireless device is it, and how is it attached to your PC?
Also, what do you get if you run ifconfig eth0 and iwconfig eth0 before you run wlassistant?

Thanks for the reply..

```
rich@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:12:17:74:43:C6
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:fdcfe000-fdd00000

rich@ubuntu:~$ iwconfig eth0
eth0      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have not given up on this at all, I have just been searching this forum and Google looking for answers in an attempt to fix this on my own so that I may better understand Linux. Since my first post I have changed most everything in my configuration. I found on the dslreports forum that pppoe is not needed with my modem/router combo so I used synaptic to remove it. The original error messages concerning a bad device was corrected by commenting out some stuff in my xorg.config file concerning a waco tablet. 

So now I am using dhclient. My eth0 is now activated on start up but does not connect to the router. I suspect the problem may be some left over configuration from my cable modem. My lease file contained information about my old connection so I deleted it and Linux made a new file for me with the correct information. Once I get the network started with wlassistant then everything is good. I can stop and restart the connection with no problem. 

My network card is a wireless PC card, Linksys ( broadcom ) and worked perfect untill I switched to DSL. 
I am using WEP ( open ) and have checked the routers settings to make sure I was in fact WEP open. 

This is my current terminal window output when running wlassistant.
```
rich@ubuntu:~$ sudo wlassistant
Password:
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

Wireless interface(s): eth0
Permissions checked.
ifconfig_status: /sbin/ifconfig eth0
scan: /sbin/iwlist eth0 scan
Networks found: 1
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp/dhclient.leases
Gateway address: xxx.xxx.x.xxx
==>stderr: connect: No such device
kill_dhcp: /sbin/dhclient -r eth0
==>stderr: Internet Software Consortium DHCP Client
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit http://www.isc.org/dhcp-contrib.html

Usage: dhclient [-c] [-d] [-e] [-p <port>] [-lf lease-file]
       [-pf pidfile] [interface]
exiting.
ifup: /sbin/ifconfig eth0 up
iwconfig_set: /sbin/iwconfig eth0 mode managed channel 6 key open 1234567890 ess id 2WIRE000
iwconfig_ap: /sbin/iwconfig eth0 ap 00:00:00:00:00:00
ifconfig_dhcp: /sbin/dhclient -q eth0
Checking for active connection.
Active connection found.
Checking for active connection.
Active connection found.
Internet now accessible.
Application options saved.
Kernel socket closed.
rich@ubuntu:~$

```

I would like to know what that -q switch means upon starting my network card.
Also anyone know what kbuildsycoca is?
I ran sudo kbuildsycoca to see what would happen and got
```
rich@ubuntu:~$ sudo kbuildsycoca
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!

```
So whatever it is its apperantly usless?

Any ideas anybody?

Thanks
Rich

---

### Post by Rich3077 on 2006-07-27
Ahh I just Googled kbuildsycoca and found its a KDE configuration tool. This sounds like something I dont need as I am using Gnome. I tried looking for it via synaptic so I could remove it and synaptic didnt find any results for my search. It possible that this may even be my problem.

---

### Post by Rich3077 on 2006-07-28
[edit]Edited to say the problem is fixed. I just switched my router to 
WEP-Shared and rebooted, everything works[/edit]




Okay I am on a roll here. I uninstalled wlassistant to see if that was messing with the network manager. Afterwards I was unable to connect to the internet and also unable to re-install wlassistant. So I started thinking.. what is the differance between network manager and wlassistant? The only thing I could think of was that wlassistant had an option for "open" or 
"shared Key" network. ( mine is open ) so after some playing around with iwconfig I finally was able to connect using the commands..

root@puter2:~# iwconfig eth0 enc 1234567890 open

followed by

root@puter2:~# dhclient eth0

And I have an internet connection!! However on reboot this connection is lost.. but there must be a way to save these settings??

*Note I also changed my computer name to be the same as in windows on this machine, I dont really know if that mattered or not. 

Okay its 7 AM and I have been working at this for many hours.
Tomorrow night when I log on I hope to be thanking one of you for telling me how to save these settings. :)

Thanks 
Rich

---

