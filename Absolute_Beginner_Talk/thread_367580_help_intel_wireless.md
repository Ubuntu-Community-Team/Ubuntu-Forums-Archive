---
title: "help intel wireless"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by nilow on 2007-02-22
i have this intel wireless card i think, i have net when i plug a net cabel in to my computer by when i try installing netmanager then all net goes by by... im a noob on ubuntu and have no idea what i can do... plzz help me

---

### Post by Ben Sprinkle on 2007-02-22
Try to explain a bit more please. :)

---

### Post by nilow on 2007-02-22
i dont know what more there is to it, i type
sudo apt-get install network-manager-gnome
then it installs it and then i dont have any net. not when i reboot ore anything. so i have installed ubuntu some times now and im good at that... but the net manager dont wona work so i can go wireless wich would be a good thing for a zepto laptop to do...

---

### Post by mikewhatever on 2007-02-22
Hi,
can you please post the output of
> sudo lshw | grep -network from the terminal (Applications->Accessories->Terminal) and explain exactly what's wrong.

Regarding the above post, you do have some kind of connection, right? Is it wired or wireless?

---

### Post by nilow on 2007-02-22
Password:
155:           *-network  
191:           *-network DISABLED
193:                product: PRO/Wireless 3945ABG Network Connection

---

### Post by Ben Sprinkle on 2007-02-22
I just don't understand, sorry. Maybe someone else will know your answer. :)

---

### Post by nilow on 2007-02-22
but there is trouble in there right?
(btw i haven't installed netmanager atm because i only have one computer...)

---

### Post by mikewhatever on 2007-02-22
Can you please explain very very clearly what is the problem. I assume there is one or you wouldn't be asking. What kind of connection do you have now? What are you trying to achieve and can't?

---

### Post by nilow on 2007-02-22
im on a plug ore what it is called, i wont wireless to work.
i tried to get network-manager-gnome from terminal by saying
sudo apt-get install network-manager-gnome
after that all my internet even from the cabel goes bey bey

---

### Post by Ben Sprinkle on 2007-02-22
Reset your dhcp from your router, then restart your computer.

---

### Post by nilow on 2007-02-22
what? i dont know how to do that from ubuntu
can you tell me what to do from terminal?

---

### Post by Ben Sprinkle on 2007-02-22
Click one of these, tell me if you get a thing asking for a username and password.
[http://192.168.15.1](http://192.168.15.1)
[http://192.169.1.1](http://192.169.1.1)
[http://192.168.0.1](http://192.168.0.1)

---

### Post by nilow on 2007-02-22
the one in the middle take some time to open, the other ones just pop and say that they dont work

---

### Post by mikewhatever on 2007-02-22
Right, correct me if I got it wrong: you had wired/cable connection and wanted to use the wireless, there fore installed network manager, and the problem is, that now, neither wired nor wireless connections work.

Does the network manager icon appear on the top panel next to the clock? Can you see the available networks by clicking on it? If you go to System->Administration->Networking, is there a wireless setup option? Can you post the output of iwconfig from the terminal.

---

### Post by nilow on 2007-02-22
i dont get the icon op at the top right the outcome is

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9564   Missed beacon:0

sit0      no wireless extensions.

---

### Post by nilow on 2007-02-22
sorry about the smileys

---

### Post by nilow on 2007-02-22
do you know what the problem is?

---

### Post by mikewhatever on 2007-02-22
The problem with the wireless may be that you have to install linux-restricted-modules for you kernel. You'll need your wired connection to get the package directly from synaptic, or download it from [this page]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all") on another PC. To check you kernel version, type uname -r in the terminal.
I don't know why the wired doesn't work, or why the NT icon doesn't show up.

---

### Post by nilow on 2007-02-22
i have a wire conection atm. what do i write in terminal to get it installed?

---

### Post by tcebak on 2007-02-22
hey, i think i had the same problem. you may need to install ndiswrapper. even though links are no fun here is one [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) but someone may be able to tell you more!

---

### Post by nilow on 2007-02-22
that guide don't make no sense to me, isn't there a simple way to do it when i have a wire conection?

---

### Post by nickoli_02 on 2007-02-22
Type this in a terminal and post the output:

```
lspci | grep Network

```

You shouldn't need the network manager to get a wireless connection. Also, if you do have an Intel wireless card it should be pretty easy to get working. It's most likely a configuration issue. When you go to System -> Administration -> Networking, do you see a wireless connection? If yes you can configure it by selecting it and clicking Properties. Configure it with your network SSID, WEP password, and choose either static IP or DHCP. You'll most likely want DHCP. 

A note on the password, if you use WPA for your wireless password encryption you'll have to go through some more configuration options with wpa_supplicant. I'd advise sticking with WEP until you get your network up and running, then if you want WPA then configure it later.

---

### Post by nilow on 2007-02-22
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

when i use that way of getting net i can't get the code to work... very wird...

---

### Post by nickoli_02 on 2007-02-22
Use what way, and get what code to work? Post more detailed replies and you'll get help much quicker.

---

### Post by nilow on 2007-02-22
when i go in System -> Administration -> Networking then take the wireless go to properties ore how it is, then i type in the net key then disconect the wire then i have no net, i have tried all of the difrent ways that it gives me...

---

### Post by nickoli_02 on 2007-02-22
In the networking window, make the default gateway eth1 instead of eth0, and try again.

---

### Post by nilow on 2007-02-22
i cant see where in there i should do that...

---

### Post by nickoli_02 on 2007-02-22
At the bottom of the window, it says

Default gateway device: <choose eth0/eth1>

---

### Post by nilow on 2007-02-22
sorry it doesn't, maybe it because i use it on danish ore somthing, but i cant find one that say anything like that, in danish of curse

---

### Post by nickoli_02 on 2007-02-22
That is odd... post the output of ifconfig and iwconfig

---

### Post by nilow on 2007-02-22
nilow@sorbon1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:5C:7C  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fec1:5c7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:208654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:288787930 (275.4 MiB)  TX bytes:12492832 (11.9 MiB)
          Interrupt:169 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:DD:93:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:208296 errors:0 dropped:10331 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:ce000000-ce000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8182 (7.9 KiB)  TX bytes:8182 (7.9 KiB)

nilow@sorbon1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"haldur"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10331   Missed beacon:0

sit0      no wireless extensions.

nilow@sorbon1:~$

---

### Post by nickoli_02 on 2007-02-22
Your wireless interface hasn't acquired an IP from your router. If you're sure your eth1 properties are set up correctly try this:

```
sudo ifdown eth1
sudo ifup eth1
```

to restart the wireless interface. Now post the output of ifconfig.

---

### Post by nilow on 2007-02-22
nilow@sorbon1:~$ sudo ifdown eth1
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 29277
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:dd:93:3f
Sending on   LPF/eth1/00:13:02:dd:93:3f
Sending on   Socket/fallback
nilow@sorbon1:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
nilow@sorbon1:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:dd:93:3f
Sending on   LPF/eth1/00:13:02:dd:93:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
nilow@sorbon1:~$ 
nilow@sorbon1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:5C:7C  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fec1:5c7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:289361831 (275.9 MiB)  TX bytes:12654194 (12.0 MiB)
          Interrupt:169 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:DD:93:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:215978 errors:0 dropped:10390 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:ce000000-ce000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8182 (7.9 KiB)  TX bytes:8182 (7.9 KiB)

nilow@sorbon1:~$

---

### Post by nickoli_02 on 2007-02-22
your wireless card isn't talking to your router. Or, they are talking, but the router is rejecting your authentication. Try disabling your wireless security on your router and in the networking preferences in Ubuntu, and try again. Also make sure your router is set to DHCP, as well as in network preferences. If we can get your card to connect with the router without wireless security it should be pretty easy to get them to talk with WEP as well.

---

### Post by nilow on 2007-02-22
i have no idea how to do that... its not me that sat the router op... but i have been on the router one time before with a program (on ubuntu) where i just typed the code and then if worked...
i dont know why i cant do that now...

---

### Post by nickoli_02 on 2007-02-22
I don't know what you mean by "typed the code". 

In your browser, try navigating to [192.168.1.1]("192.168.1.1"). It's a pretty common IP for a router. If it asks for a password, try some combinations of "root" and "admin".

---

### Post by nilow on 2007-02-22
ok i killed the wireless security and then i did the same as you have asked me before... the terminal is here:
nilow@sorbon1:~$ sudo ifdown eth1
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 383
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:dd:93:3f
Sending on   LPF/eth1/00:13:02:dd:93:3f
Sending on   Socket/fallback
nilow@sorbon1:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:dd:93:3f
Sending on   LPF/eth1/00:13:02:dd:93:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
nilow@sorbon1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:5C:7C  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fec1:5c7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:450094140 (429.2 MiB)  TX bytes:16945804 (16.1 MiB)
          Interrupt:169 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:DD:93:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:243420 errors:0 dropped:10477 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:ce000000-ce000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30394 (29.6 KiB)  TX bytes:30394 (29.6 KiB)

nilow@sorbon1:~$

---

### Post by nickoli_02 on 2007-02-22
Your card and router still aren't talking. Make sure you have the SSID right and DHCP is enabled on the router and in your wireless settings.

If the SSID is right and DHCP is on, try turning DHCP off and assigning a static IP to your computer. And of course, do the whole ifdown, ifup thing.

---

### Post by nilow on 2007-02-22
i did as you said... what is it in this log that if going to chance, when it works?

nilow@sorbon1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:5C:7C  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fec1:5c7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:588520591 (561.2 MiB)  TX bytes:20569393 (19.6 MiB)
          Interrupt:169 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:DD:93:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:244181 errors:0 dropped:10478 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:ce000000-ce000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48559 (47.4 KiB)  TX bytes:48559 (47.4 KiB)

nilow@sorbon1:~$

---

### Post by nilow on 2007-02-22
forgot the if down if up thing...
eth1      Link encap:Ethernet  HWaddr 00:13:02:DD:93:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247256 errors:0 dropped:10479 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:ce000000-ce000fff

---

### Post by nickoli_02 on 2007-02-22
If your card and router are talking, you'll get an inet address in eth1. Here's mine as an example:

```
$ sudo ifdown eth1
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:12:f0:86:b4:0c
Sending on   LPF/eth1/00:12:f0:86:b4:0c
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67

```

```
$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:12:f0:86:b4:0c
Sending on   LPF/eth1/00:12:f0:86:b4:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.115 -- renewal in 35664 seconds.

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:81:B1:2A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:12:F0:86:B4:0C
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe86:b40c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126074 errors:0 dropped:166 overruns:0 frame:0
          TX packets:103632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:132857265 (126.7 MiB)  TX bytes:14522930 (13.8 MiB)
          Interrupt:50 Base address:0x4000 Memory:c8216000-c8216fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:720 (720.0 b)  TX bytes:720 (720.0 b)

```

I don't know why your card and router aren't talking... :confused:

---

### Post by nilow on 2007-02-22
can i have you msn ore skype ore somthing then we can do this easyer... then et dont take like 45 min par reply

---

### Post by nickoli_02 on 2007-02-22
Sorry, I'm stumped... this has got to be a configuration issue, it seems your wireless driver is working fine. Start from [this]("https://help.ubuntu.com/community/NetworkDevices") page in the wiki, maybe you can find something helpful there. Good luck, sorry I couldn't help you further

---

### Post by nilow on 2007-02-22
thank you fore the help :) and no worry about that we didn't get it all done...

---

### Post by i.am.canadian on 2007-02-22
Hi there,

You had said that you don't have an icon for the network-manager in your display area next to your clock (in GNOME it should be in the top right near the shut down button).  What you might want to try this: go to system (next to places in the top left) and then go to Preferences and then to Sessions.

Select 'Startup Programs' from the tabs along the top (third one from the left) and hit 'Add'

Now enter 'nm-applet' (without the quotation marks obviously ;))

Now logout and log back in.  Now you should have an icon in the display area.  It should look like two overlapping flat-panel monitors if you have a wired connection.  If you click on it it should give you a drop down menu of the wireless connections available.  There will be a little shield if it is protected by a password.  I have been able to use mine to connect to WEP, WPA and WPA2.

I hope this helps.  I seems like something that hadn't been suggested yet.

Cheers.

---

