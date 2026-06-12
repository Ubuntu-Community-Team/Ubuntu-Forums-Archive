---
title: "Network Setup"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by sthilges on 2007-06-02
Hello,

My problem is I can't connect to the internet.  In my apartment building I connect to the internet through sonicwall.  Then I share the internet between my laptop and my desktop with my linksys router.  I was running xp on both of my computers and I could connect to the internet fine, but I recently wanted to switch to linux so I installed ubuntu on my desktop.  The internet still works fine on my laptop but I can't connect on my desktop.  I couldn't connect to my router either.  I would appreciate any help on solving this problem, I really want to avoid using windows but I need the internet.

Thanks,
Sam

I ran ifconfig in a terminal and this is the result:
eth0     Link encap:Ethernet  HWaddr 00:19:21:5c:52:96
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0,0 b)  TX bytes:0 (0,0 b)
            Interrupt: 22  Base address:0x4000

eth0:avah
           Link encap:Ethernet  HWaddr 00:19:21:5c:52:96
           inet addr:169.254.5.166  Bcast:169.254.255.255  Mask:255.255.0.0
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           Interrupt:22  Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:  ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 tqueuelen:0
          RX bytes:60372 (58.9 KiB)  TX bytes:60372 (58.9 KiB)

---

### Post by TwistesdTexan on 2007-06-03
What version of Ubuntu do you have? Dapper,Edgy,Fiesty? And what brew? Xubuntu,Kubuntu,or Ubuntu?

Next question
What is the model of your linksys router?

I don't think I can halp but these are questions that someone will need to help.

---

### Post by sthilges on 2007-06-03
I installed ubuntu 7.04 Feisty Fawn-amd64 and am using a Linksys router model no WRT54GS.

---

### Post by TwistesdTexan on 2007-06-03
Thanks Dave-5B. I haven't set up my network since Breezy!

---

### Post by dave-5B on 2007-06-03
If xp connected to the internet with no probs then you can probably just look in:
System > Admin > Network
and set it to automatic or zeroconf
there should be no need to fiddle around too much (unless there is something i'm missing), improved automatic network configuration wa one of the major new features in feisty

---

### Post by BatteryCell on 2007-06-03
Also could you post the results of:
```
cat /etc/network/interfaces
```
```
cat /etc/resolv.conf
```

---

### Post by sthilges on 2007-06-03
No, and I tried to ping the router at 192.168.1.1 and it said,
     From 169.254.5.166 icmp_seq=1 Destination Host Unreachable

---

### Post by sthilges on 2007-06-03
the network was already set on automatic, but I tried Zeroconf too and that didn't work


the result of cat /etc/network/interfaces is:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

the result of cat /etc/resolv.conf is:
cat: /etc/resolv.conf: No such file or directory

---

### Post by dave-5B on 2007-06-03
personally i have always setup my network using static ip's (because i didnt know how to do dhcp back when i used slackware :) ), so on that front i have no idea. Here are some (possibly erroneous) thoughts:

does the router have any documentation which says what ip address it will take (mine is 192.168.0.1), try pinging (or logging in via your browser) from windows too

your desktop has obviously decided at some point that its ip is 169.254.5.166 (this is in your dump from ifconfig as well), i have no idea how or why

---

### Post by BatteryCell on 2007-06-03
Hmm, well thats a problem.  The no resolv.conf means that your computer can't resolve dns names (google.com for instance).  Usually dns servers are provided by your isps, and you might want to try a couple of things.  Unfortunately I use kubuntu and it's been a while since I've used gnome, so I don't remember the graphical tool that you can use to set up dns servers.  However, you can always just add them manually.  You need to create a file resolv.conf and add the nameservers. The file should appear like:
```

search xxx.xxx.xxx.xxx.
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```
Of course replace the xs with your isp's nameservers. For instance one of mine is 68.87.64.196, so it would be:
```
nameserver 68.87.64.196
``` 

The search line is not really that important, it has to do with hostnames that don't contain a dot (so if you did ssh me@myplace it would search whatever server you told it to for myplace since there are no dots).

Then just save the file as /etc/resolv.conf

And restart networking :
```
/etc/init.d/networking restart
```

If you don't know your nameservers call you isp.  

Hopefully your internet should work.

---

### Post by dave-5B on 2007-06-03
here is a dump of my /etc/resolv.conf
> david@lyra:~$ cat /etc/resolv.conf
nameserver 203.2.75.132
nameserver 198.142.0.51

those two addresses are the nameservers of my isp, but im sure that is not the proper way to set it up, it should be the address of your router i think

EDIT: listen to BatteryCell over me!
EDIT2: the graphical tool is in System > Admin > Network

---

### Post by sthilges on 2007-06-03
My router's ip address is 192.168.1.1, which I can still log into from windows on my laptop, but I tried with ubuntu on my desktop and it won't work.  I also tried to ping my router and that failed.

---

### Post by TwistesdTexan on 2007-06-03
System>Administration>Network. Then the DNS tab. Add and enter you router's IP address. Also any other computers that you have on the network.

---

### Post by KMW on 2007-06-03
When I was setting up my wireless I ended up resetting the router to defaults then reconfigure it then reboot the cable modem and router and then it worked. You could try that.

---

### Post by sthilges on 2007-06-03
KMW - I reset my router and tried to connect, but that didn't work.
Texan - I added 192.168.1.1 to the DNS tab and then I tried to connect to the router, but no go.
BatteryCell - If I call my isp and ask them for the nameserver address then should I add it to where texan said and that should work? or do I need to create the resolv.conf file?

---

### Post by TwistesdTexan on 2007-06-03
Try to reconnect. Sometimes the router takes time to recognize the change. I have a linksys WRT54G also.

---

### Post by BatteryCell on 2007-06-03
Yes you should add them to the tab, and it should automatically create the file (also I don't see how setting your router as a dns server would help but...).  Also, you can always try our dns servers, they should technically still work, its just that you aren't 'sposed' to.
mine are:
```

nameserver 68.87.66.196
nameserver 68.87.64.196
nameserver 68.87.73.242

```

Also are you by any chance using wireless, or is this a hardline (cable)?

---

### Post by Mr.Beast on 2007-06-03
O.K., I don't know a huge amount about Ubuntu and its' network configuration settings (have a chuckle, as I don't know how to set a static address ;-) however networks I am a bit more knowledgable on (in general.)
Firstly, don't get hung up on the DNS / names thing, at this stage it's not (I don't think...) your biggest problem.

You need to get a valid TCP/IP address with the right subnet mask onto your UBUNTU machine.  
The 169.254 address us an automatically assigned range, and "may" not have come from your DHCP server, 
(Windows does this as well, in this range so that if there is no DHCP infrastructure and workstations get together (like a LAN PARTY say) they can still talk together).

Just to let you know that I have a hard wired network port, and I have a wireless card, and when I do an ifconfig I get
ath1      Link encap:Ethernet  HWaddr 00:nn:nn:nn:nn:nn  
          inet addr:10.0.0.29  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe4c:870c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1108091 (1.0 MiB)  TX bytes:79431 (77.5 KiB)

eth0      Link encap:Ethernet  HWaddr 00:nn:nn:nn:n:nn  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-4C-87-0C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21686 errors:0 dropped:0 overruns:0 frame:1048
          TX packets:1118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3224389 (3.0 MiB)  TX bytes:131308 (128.2 KiB)
          Interrupt:11 

It looks to me that my install is not giving out the 169.254 to my eth0 (hard wired)
Also, I seem to have a wifi interface, and my ath0 interface.

I think your problem is more in this area, than in DNS.   try a wired cable and I reckon that'll get you online to start with.



it would really help if you could post the IPCONFIG /ALL from your XP machine, as this is working at the moment.
(you can do IPCONFIG /ALL >>C:\ip.txt  and this will create a dumpfile called ip.exe in the root of the c drive that you can upload, or you can do a screen print.)

I also assume that you are trying to use wireless to connect, any chance you can use a cable directly to one of the network ports?  
Does your router use WEP /WPA or a password, does it have other restrictions (Mac address, tied to NODENAME perhaps?)
Also, if you post your ISP, I'm sure that someone can find out what their DNS servers are for you, or you could check it out on your XP box, but in general, your router should have these in, and you should have your router as your DNS server. (In case you may want to connect  to your XP box by it's name.)

I downloaded network-manager and this sorted out my wireless stuff out the box.

---

### Post by sthilges on 2007-06-03
I am using a wired ethernet connection.  I ran ipconfig/all on my laptop and attached the results.  Also I found this link about 169.254.xxx.xxx:
     [http://homepage.ntlworld.com/robin.d.h.walker/cmtips/badip.html#ip169](http://homepage.ntlworld.com/robin.d.h.walker/cmtips/badip.html#ip169)
does this have something to do with the sonicwall I have to log into to get on the internet in my apartment building?

---

### Post by BatteryCell on 2007-06-03
> 
eth0 Link encap:Ethernet HWaddr 00:19:21:5c:52:96
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0,0 b) TX bytes:0 (0,0 b)
Interrupt: 22 Base address:0x4000

Tells me that it is bringing up the interface, it just cant assign it an address nor can it contact dns servers.  So, make sure in the gnome utility that the dhcp is assigning it an ip.  You can also run :
```

sudo killall dhclient3
sudo dhclient3

```

And show us the output (it will help tell us what the problem is with the unassigned ip on eth0).

---

### Post by sthilges on 2007-06-03
I ran sudo killall dhclient3 and then sudo dhclient3 and here is the output:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:21:5c:52:96
Sending on LPF/eth0/00:19:21:5c:52:96
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by sthilges on 2007-06-04
Well, thanks for the help everyone that tried.  I'm just going back to xp since it worked.

---

### Post by sthilges on 2007-06-05
nevermind, as i was installing xp and surfing the forums on my laptop i found this:
    [http://ubuntuforums.org/showthread.php?t=276041&highlight=et131x](http://ubuntuforums.org/showthread.php?t=276041&highlight=et131x)
and it turns out i didn't have the right driver. So i followed there instruction and I know have internet on ubuntu!!!
Thanks again for all the help.

---

