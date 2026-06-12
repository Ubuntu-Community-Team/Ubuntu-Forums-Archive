---
title: "Hardware probs with edgy on Acer 2310"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by MikeAK on 2007-02-13
Hi,

I have just installed Edgy on my Acer Travelmate 2310. The installation went very well with dual booting with XP working perfectly. However I found I could't get updates because the WIFI conection isn't working. Went round to a friends house to use his wired connection to get updates hoping that would solve it. First problem was DHCP didn't work, but set static ip to get round that (DHCP worked when running XP so the server is running on his network), succesfully updated system.

The Atheros 5005G wifi network card appears in the network settings application which I have setup with a static ip address, also set dns and gateway setting (to exactly the same settings as used when booted in XP where everything works). If I look at my wireless access points status, using another PC while my laptop is running ubuntu I can see the Atheros mac address registered. The signal strength icon at the top of the ubuntu desktop  is green and if I click on it I see approx 85% signal strength. This also shows packets transmitted and received, if I try to browse to google I see packets transmitted but not a single packet is ever recieved. If I try to ping another PC on my local network same thing, packets transmitted but none received.

The video resolution is incorrect. Native resolution of the laptop is 1280x800, the highest resolution I am offered is 1024x768. I tried eding xorg.conf to add 1280x800 but this had no effect. I also downloaded an installed (I think!) the SIS 661 driver from the winischhoferas website suggested else where in these forums but this also had no effect.

The Synaptic trackpad only works as basic mouse, none of the "advanced" functions like tap to click work. I have not looked into this yet, considering my lack of success with the previous two problems I thought I'd better get some advice first.

Please forgive me if I am missing something basic but I am very new to Linux and am still at the stage where every time time I want to try to change somthing I find I need to know 10 other things in order to do it!

Thanks

Mike

---

### Post by MikeAK on 2007-02-13
I saw this in another post

Have you tried installing gsynaptics: 
Code:
sudo apt-get install gsnyaptics.Once installed, you'll get Touchpad entry under System->Preferences. To open it, you'll need to add this line: 
Code:
Option "SHMConfig" "true"to the touchpad section of your /etc/X11/xorg.conf file.
sudo aptitude install gsynapticsits a GUI and will allow you to configure your touchpad

But I just got message Can't find package gynaptics

Anyone any ideas on the wifi and screen problems?

---

### Post by MikeAK on 2007-02-13
Looked a bit further and tried ifconfig. This gave 4 devices ath0, eth0, wifi0 and sit0. The network configuration application only shows ath0 and eth0 what are the other two?

The wifi0 shows many thousands of packets sent and recieved while ath0 shows a few hundred sent and none recieved. I'm confused! Which of wifi0 and ath0 is my wifi adapter or do they work together?

One of the hardest things I am finding with Linux is getting an overall picture. There is lot of detail on individual things, but not much at least as far as I can find, which gives an overall view of the major components of the operating system and how they interact. Any pointers to such information would be very welcome.

Thanks

Mike

---

### Post by annda on 2007-02-13
what about iwconfig? what does that say?

---

### Post by MikeAK on 2007-02-14
Thanks for the reply. Below is output of iwconfig and ifconfig

michael@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MKCKNET"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:CB:A4:51:7A   
          Bit Rate:48 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


michael@ubuntu-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0E:9B:B2:2A:CE  
          inet6 addr: fe80::20e:9bff:feb2:2ace/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:6966 (6.8 KiB)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:94:34:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:648 (648.0 b)  TX bytes:648 (648.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0E-9B-B2-2A-CE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1343905 (1.2 MiB)  TX bytes:13975 (13.6 KiB)
          Interrupt:225 Memory:eca60000-eca70000


Thanks

Mike

---

### Post by annda on 2007-02-14
ok, so your wireless is atheros (ath0) and you seem to have configured it to pick up your network (ESSID:"MKCKNET"). but you do not get an IP from your router (no inet addr, only inet6 addr).

what happens when you type
```

sudo ifdown ath0
```

and then

```
sudo ifup ath0
```

can you get an IP address or do you get DHCP errors?

this is very comprehensive:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by MikeAK on 2007-02-14
Did ifup and ifdown, screen dump below as you can see dhcp failed. Also looked at /etc/network/interfaces, I suspect the ip address you see there is from when I tried a static ip address previously, it is the address I entered and is not in the dhcp range, static ip aslo did not work.

What are eth1 and  eth2? I only have one wired ethenet connection.

What is wlan0? I have now seen wlan0, wifi0 and ath0 in various files. what are they?




michael@ubuntu-laptop:~$ sudo ifdown ath0
Password:
There is already a pid file /var/run/dhclient.ath0.pid with pid 4430
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0e:9b:b2:2a:ce
Sending on   LPF/ath0/00:0e:9b:b2:2a:ce
Sending on   Socket/fallback
michael@ubuntu-laptop:~$ sudo if up ath0
sudo: if: command not found
michael@ubuntu-laptop:~$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0e:9b:b2:2a:ce
Sending on   LPF/ath0/00:0e:9b:b2:2a:ce
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
michael@ubuntu-laptop:~$ 


Contents of /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid MKCKNET
wireless-key s:lauren29james
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0
iface wlan0 inet dhcp


auto eth0


Sorry about the delay replying I have to keep dual booting back to XP to use the internet to check forum!

Thanks

mike

---

### Post by annda on 2007-02-14
eth1 etc. seem to be some default devices, you can comment them out (using # at the beginning of each line).

can you switch off encryption in your router for some testing? if you can, comment out all the lines after iface ath0........

see if you can configure network (system > administration > network) to work. some serious rebooting might be necessary. most of the times 
```

sudo /etc/init.d/networking restart
```

will do, but it's safer to reboot (especially GUI tools seem to ignore on-the-fly configuration changes).

going to sleep now but help will come. good luck!

---

### Post by MikeAK on 2007-02-15
OK managed to get encryption turned off for a few minutes to test. Connection worked OK got address via dhcp and could get to google in firefox. Encryption is now turned back on I can't leave it of for further tests as several other people use the router and there is a lot of wifi activity in this area. Router encryption is WPA using private shared key. I have had a google round and it seems there may be problems with WPA and Ubuntu (Linux in general?). As recommended by another post I did apt-get install network-manager and apt-get install network-manager-gnome these completed successfully but I am usure as to what to do next.

Thanks

Mike

---

### Post by annda on 2007-02-15
do you see a network manager applet in your panel after reboot? if not, right click on the panel and add the applet. you should be able to configure your settings from there.

from [WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo"):

> For Ubuntu 6.06 LTS (Dapper) or later (but not for Kubuntu 6.06 or 6.10), there should be a Network Manager icon in the GNOME panel, which looks like a couple of dots. Right click the Network Manager icon to enable the network if necessary. Next, left click on the Network Manager icon and choose "Connect to other wireless network". Then, enter "YOUR-SSID" for the network name and choose your type "WPA ENTERPRISE" or "WPA PERSONAL" etc, etc ... for wireless security. Enter the password in the password text entry box. Click connect to attempt a connection.

---

### Post by MikeAK on 2007-02-15
Hi, No icon in tray, tried adding but its not in the list and the search does not find it. tried apt-get again which says its installed and up to date. Ran sudo NetworkManager prompt returned after couple of seconds no errors. Still no icon and cant find in search. 

Mike

---

### Post by MikeAK on 2007-02-15
Sorry bit confused there! Icon loks like two computers (at least to me!). It only seems to know about the wired adapter. I have rebooted (twice) but still the same.

---

### Post by annda on 2007-02-15
tried clicking or right-clicking on it (sorry, feisty comes with a newer version, it's a little different here)? if i remember right, after some clicking you finally get to see a button "configure" and it will take you to a tool that lets you configure wired/wireless/dialup. i believe you can also find it in the system menu under network or networking or something like that.

if that does not help, i think it would be a good idea to post a new thread asking for help with the network manager on edgy and wpa. people without an acer laptop may not be reading this, but they have much more experience than me (plus the right software to tell you the exact steps).

and keep up the spirit!

---

### Post by MikeAK on 2007-02-15
OK Ill do that. Thanks for all your help so far. I think its nearly there now.

Mike

---

