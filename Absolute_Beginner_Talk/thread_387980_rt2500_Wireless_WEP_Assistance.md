---
title: "rt2500 Wireless WEP Assistance"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-03-18
I've been working on this wireless issue for a while.  Here's my ifconfig info:
leah@leah-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:25:0B:52  
          inet addr:192.168.254.11  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe25:b52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24505 (23.9 KiB)  TX bytes:10048 (9.8 KiB)
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ra0       Link encap:Ethernet  HWaddr 00:11:09:0B:D8:46  
          inet6 addr: fe80::211:9ff:fe0b:d846/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:865830 (845.5 KiB)
          Interrupt:11 Base address:0x8000 

leah@leah-laptop:~$ 

And here is my iwconfig info:

leah@leah-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"MYNETWORK"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

leah@leah-laptop:~$ 


The wired networking is working fine.  I just can't get the wireless to connect.  In Windows, wireless connects to an linksys access point, with a WEP key.  I put the key in when setting up the wireless card in Networking, and it is enabled, and turned on.   I tried to install Network Manager, but I can't get it to show up in the applications menu, and I can't figure out how to get it elsewhere.  I just want to get the wireless hooked up so I can really sink my teeth into Ubuntu.  

Please respond in newbie-speak.  I'm just starting Linux, although I know Windows like the back of my hand.  

:confused:

---

### Post by giftnudel on 2007-03-19
Hi,

for network-manager, you can run ```
nm-applet
``` in a terminal.

If you want to do that in the console, you need to make sure, that you choose the correct mode. If you have a hexadecimal key (looking similar to 122E-24AF-D215-...), you can do ```
sudo iwconfig ra0 essid "MYNETWORK" enc 122E-24AF-D215-...
``` but if you have a string key (looking like "thisismypassw") you need to use the ASCII key with ```
sudo iwconfig ra0 essid "MYNETWORK" enc s:thisismyopassw
```

You then need to get an ip address. With dhcp, this is dead-simple:
```
sudo dhclient ra0
```

Questions, remarks? Just ask.

giftnudel

---

### Post by thefoolisme on 2007-03-19
Thanks for the response.  I did as you suggested, but nothing appeared to happen, except that I now have two "Wired connection" icons in the top right of the screen.  Here's a pasting from Terminal:

leah@leah-laptop:~$ nm-applet
sudo iwconfig ra0 essid "MYNETWORK" enc e7227c55be9b41xxxxxxxxxxxx
sudo dhclient ra0


I then closed the terminal, reopened it, and just tried "sudo dhclient ra0" and got this: 

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:11:09:0b:d8:46
Sending on   LPF/ra0/00:11:09:0b:d8:46
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
leah@leah-laptop:~$ 



I never got a message confirming the wireless connection.  I tried this while plugged into the wired network, and while not being connected to the wired network.  When doing it while not being connected to the wired network, and having nothing appear to happen, I plugged in the network cord, and got a message that I was no connected to the wired network.  The wireless card is enabled under "Networking", so I'm not sure what the problem is.  I don't see my wireless access point in iwconfig though.  Could this be the problem, and if so, how to fix it?

Next suggestion?  :-)

---

### Post by giftnudel on 2007-03-19
Well having two wired-networking icons means nm-applet was already started. 
You should go in the networking manager accessible via the menu system->administration and should put your wireless connection in the same (exact same) state as your wired connection, it can then be managed by network-manager.
Then just klick on the wired icon and choose connect to wireless (this only works when not on the line)

If this doesn't work, please show your /etc/network/interfaces file (be careful if there is a password in there)

Good luck,
giftnudel

---

### Post by oilchangeguy on 2007-03-19
please go to system, admin, networking. and advise what is showing in networking. you should see three things. your wireless connection, wlan0, your ethernet card, eth0, and maybe a phone modem. the wired and wireless network connections should show as active. (and if you're lucky the modem will to). then from the network icon near the clock from the drop down menu select wlano, the default is lo. you'll need to enter your wep code and you should be able to get online.

---

### Post by thefoolisme on 2007-03-19
Under system/Admin/Networking, there are 3 connections:  wireless connection, which is showing the ESSID I entered, and Address: DHCP; Wired Connection, with Address: DHCP, and the modem.  The two network cards are enabled.  

THe only option in the network manager icon in the top right is for wired network, which is greyed out at the moment because the cable isn't plugged in.  

This is what's showing in my /etc/net/interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid MYNETWORK
wireless-key e7227c55be9b4140XXXXXXXXX

auto ra0



auto eth0


I appreciate the help, and will appreciate it even more if we can get this up and running!  lol

---

### Post by jrandolph on 2007-03-19
I had almost the same trouble as you I also have a Linksys router a Linksys wireless pci card I know u are on a laptop but maybe this thread will help.  It is how I got mine working

[http://ubuntuforums.org/showthread.php?t=380221](http://ubuntuforums.org/showthread.php?t=380221)

It is worth a try

I know i was banging my freakin head against the wall with this

---

### Post by giftnudel on 2007-03-19
well, just remove the three lines above auto ra0 and it should appear in network-manager (maybe need to do ```
sudo /etc/dbus-1/event.d/25network-manager restart
``` before it shows up)

giftnudel

---

### Post by dstew on 2007-03-19
Are you sure that wireless key is correct?

---

### Post by thefoolisme on 2007-03-19
Itried deleting the stuff in network/interfaces.  I then tried restarting Network Manager, but got this message:

leah@leah-laptop:~$ sudo /etc/dbus-1/event.d/25network-manager restart
sudo: /etc/dbus-1/event.d/25network-manager: command not found
leah@leah-laptop:~$ 

So I restarted the computer, thinking that would do it, but it still only has wired networking as an option in the Network Manager icon.  

And as for the "Is the password correct" question, at first I was like, "Sure it is" , but I went and quadruple checked it.  It's correct.  The XXX's above are so I don't put the whole thing out there.  :-)  

I went to the link that was posted, but until I can get my wireless card to show up, I don't think that will help (I had actually seen that one before in my searches).  

No one has mentioned the access point yet.  I'm going to assume it's not a problem.  I only ask because I have seen others talking about theirs, and I don't think I've seen it show up in my setup (but I guess the wireless card has to be running right for that :-)

What's next?  I'm not working today, so I'd love to get this thing connected.

---

### Post by cwmaxson on 2007-03-19
I've had problems with network manager as well, try this, it "just works":

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Cheers!

---

### Post by thefoolisme on 2007-03-19
Wow!  Thanks for the WiCD idea.  That did it.  I'm typing from my wireless connection.  Now onward to the next hurdle!  :guitar:

---

### Post by cwmaxson on 2007-03-19
Wonderful!

---

