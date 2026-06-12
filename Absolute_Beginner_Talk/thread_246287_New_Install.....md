---
title: "New Install...."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by aran384 on 2006-08-29
I recently did a new install of ubuntu amd64.... i added it to a new partition that i cleaned up with Partition Magic on my 2nd hdd....

my second hdd is a on usb, it shows up on the system as a normal hdd....

although i think am having a few hardware problems... when ever i boot up to ubuntu i have no internet connection... 

my motherboard is a M32N32-SLI Deluxe with dual gigabit lan and wlan, everything is detected ... all my lan connections and even my wireless connection gets detected ... but i still have no internet..

i would also like help setting my boot.ini on my main hdd to boot the second hdd if i select... 

i would much appreciate some help with these matters... :)

---

### Post by Josh_b on 2006-08-29
I can kind of help with your first problem as it happens to me as well. Try deactivating/activating your network connection (**System->Administration->Networking (I think)**). That should allow you to get onto the net. You'll have to this every time. Someone else might know a permanent fix, but I have yet to find out.

The second problem is to with GRUB (kind of like boot.ini in windows). But that's about as much as I can tell you.

Hope that helps,
Josh

---

### Post by encompass on 2006-08-29
boot.ini? are you working in windows for your dual boot? eeks.
As for you issue with the internet... do you have a router... try connect threw the cable and pinging your router or another computer.
try this too..
sudo dhclient (whatever your card is... probably eth0 or eth1)
did it aquire an ip?  And what is it?

---

### Post by aran384 on 2006-08-29
i have both eth0 and eth1 

i even have a wlan0 

windows was my first install and is on my main sata drive... and has the default boot although i might switch this and then edit grub ... anit decided yet ... who ever can offer the easiest way then am happy :)

---

### Post by Josh_b on 2006-08-29
so did reactivating your network connection work?

---

### Post by aran384 on 2006-08-29
reactivating my ethernet ports failed to work and sudo dhclient failed to show anything... :( 

still stuck with no connection :(

---

### Post by Josh_b on 2006-08-29
are you using a static or dynamic ip address (did you put one in or does it automatically pick)?

---

### Post by aran384 on 2006-08-29
i did have it setup to give me one with dhcp on the router... but i deleted it to see if this would help me but it didnt help :(

am now on a dynamic ip setting...

---

### Post by Josh_b on 2006-08-29
so is windows and linux on the same hdd? Can you get onto the net after you've booted into windows, restarted and gone into linux? (Sorry if that takes a while)

---

### Post by aran384 on 2006-08-29
am in windows now... and no windows and linux not on same hdd....

my internet connection works in windows for some reason... :S

and i get my normal ip in windows that i always have...

---

### Post by Josh_b on 2006-08-29
try restarting (not shutting down) and booting into linux. That may connect linux, becuase sometimes there is an error (or so I've heard, which explains my network problems) in which the network interface doesn't connect with the dhcp/router/server properly, but by going into windows and then into linux, windows is doing that step (ie creating a session for that MAC address. That's how I understand it anyway. It may be way off)

---

### Post by aran384 on 2006-08-29
i have still had no success it getting my linux onto the internet :( 

it still hasnt worked ... i rebooted into linux from windows ... ive also rebooted from linux to linux and i set my ips manually and still no internet :(

---

### Post by Josh_b on 2006-08-29
well, sorry to say this, but your problem is beyond my scope.

Josh

---

### Post by steve.horsley on 2006-08-29
How are you expecting it to connect to the internet? Wireless, Ethernet? If Ethernet, what does that connect to? 

If you have a choice, the Ethernet may be easier to get going than the wireless, although the fact that you see a wlan00 isa  good start.

Can you try these commands and post the output to each?
ifconfig
iwconfig
sudo iwlist scan

---

### Post by aran384 on 2006-08-29
Alot of information here... and from it all i cant make shit out of it lol 

aran384@ARAN001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:A7:19:28
          inet6 addr: fe80::217:31ff:fea7:1928/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17288 (16.8 KiB)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:17:31:A7:1F:FE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9892 (9.6 KiB)  TX bytes:9892 (9.6 KiB)

aran384@ARAN001:~$

aran384@ARAN001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:A7:19:28
          inet6 addr: fe80::217:31ff:fea7:1928/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17288 (16.8 KiB)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:17:31:A7:1F:FE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9892 (9.6 KiB)  TX bytes:9892 (9.6 KiB)

aran384@ARAN001:~$
aran384@ARAN001:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Failed to read scan data : Operation not permitted

sit0      Interface doesn't support scanning.

aran384@ARAN001:~$

---

### Post by steve.horsley on 2006-08-29
OK. 

1) 
Can you confirm that you are trying to get the ethernet working? That you have a cable plugged in eth0? I guess so, because it says it has received some packets (but never sent any). But confirmation would be helpful.

2) 
Are you configured for static or DHCP address? Please post the contents of file /etc/network/interfaces so we can see exactly what's configured there.

3)
If you are trying to use DHCP, can you try the command 
sudo dhclient eth0
and post the output? 

It looks odd to me that eth0 reports having received packets but never sent any. That makes me think that it's not asking for a DHCP allocated IP address. But also, it doesn't have an IP address yet, so if it's configured for a static address, that configuration is somehow wrong.

---

### Post by aran384 on 2006-08-29
yes i am trying to get my ethernet going....


it was configured to dhcp ... but i changed it and set it to what the router had set while it was in windows mode.... (still no luck though)


auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.159


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid home

auto eth0

---

### Post by aran384 on 2006-08-29
does this help anyone else???? am still stuck with ubuntu and no internet :( really badly want to get it going and install fluxbox and then maybe xgl and some other things :D

---

### Post by aran384 on 2006-08-29
I thought i would add some information about the spec of system i am running... i did a search on Nforce and found some people saying there were problems with Nforce590 chipsets...

Well my system has one of these chipsets...

AMD Athlon X2 3800+
2Gb RAM DDR800
XFX 7900GT 256mb
1x 250gb SATA 2 
1x 250gb IDE (on usb) <---- this is the drive that my ubuntu is running from...

if any of this helps it would be great to know...

---

### Post by whizbaby on 2006-08-29
Hello!
Try:
ifconfig eth0 192.168.0.100 up

this should launch your card with the desired IP. Is there any reason not to use dhcp? If not, now type (like the others said)

dhclient eth0

what does 'ping www.google.com' give now?

---

### Post by aran384 on 2006-08-29
nope still no internet in ubuntu :( this is so unfair :(

anyone else got any more ideas???

is there a way to force linux to recheck my hardware or anything... 

or is there a way to install ubuntu without having to boot into livecd first??? cause if i would that work??

---

### Post by aran384 on 2006-08-29
Dump

---

### Post by whizbaby on 2006-08-29
Do you have a graphical network-tool in your system menu (or elsewhere, depending on your WM)? What does this say about your connection? There also should be a network-diagnostics-tool.
What does 'ifconfig' say after you tried what I suggested?
(try to be a little more informative than 'nope', otherwise it's hard to guess what's going on your machine)
I believe you only have a configuration problem, otherwise there would be no ethX.

---

### Post by aran384 on 2006-08-29
i have done that command before and u can see results of what i did before in a earlier post... 

it was excatly the same...

i have noticed that the network doesnt send anything only recieves... is there a command or config area where i can change settings or make linux rescan my hardware or something????

---

### Post by steve.horsley on 2006-08-29
There's something else horribly wrong. You have it configured for a static IP address, but ifconfig says it doesn't have and IP address (although it has an IPv6 address).


Try reconfiguring it back to DHCP, then try these two commands, and post the output:
sudo dhclient eth0
ifconfig

dhclient should transmit DHCP requests. If the ifconfig still says 0 packets send after that, then maybe you have a hardware problem. You could perhaps try a cheapie ethernet PIC card?

---

### Post by whizbaby on 2006-08-29
The command 'ifconfig' without parameters does not do anything except showing you your present configuration.
Did you really type

(1)sudo ifconfig eth0 192.168.0.100 up

literally, and typing 'ifconfig' after that still left you without an IP address? (here is the first part of an ifconfig output, to show you where it should be, I zeroed out the HWaddr)

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
---here-->inet addr:129.70.14.133  Bcast:129.70.15.255  Mask:255.255.254.0
          inet6 addr: fe80::204:e2ff:fecd:aa49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64062871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49838236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3393161838 (3.1 GiB)  TX bytes:2060217010 (1.9 GiB)
          Interrupt:193 Memory:fc8fc000-0

As long as ifconfig does not give an output with an 'inet addr' equal to your desired IP network is not 'up'. You didn't post the output of

(2)sudo dhclient eth0

I'm really trying to help you so please, does (1) leave you without IP, and what's the message of (2)? What is the IP of your router (internally)?

Why do you insist on rescanning hardware? Try
lspci
If your ethernet controller is listed, it's there! PCI bus is rescanned at boot-time, no need to do it!

---

### Post by aran384 on 2006-08-29
This is the result of doing the following commands : 

sudo dhclient eth0
ifconfig

aran384@ARAN001:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:17:31:a7:19:28
Sending on   LPF/eth0/00:17:31:a7:19:28
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
aran384@ARAN001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:A7:19:28
          inet6 addr: fe80::217:31ff:fea7:1928/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:79089 (77.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12308 (12.0 KiB)  TX bytes:12308 (12.0 KiB)

aran384@ARAN001:~$


Then i tried the 

sudo ifconfig eth0 192.168.0.100 up

and this happened 


aran384@ARAN001:~$ sudo ifconfig eth0 192.168.0.100 up
aran384@ARAN001:~$ ifconfig eth0 192.168.0.100 up
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
aran384@ARAN001:~$ sudo ifconfig eth0 192.168.0.100 up
aran384@ARAN001:~$

---

### Post by whizbaby on 2006-08-29
sudo ifconfig 192.168.0.100 up
didn't seem to produce an error message, fine.
Next, I need the output of the single
ifconfig 
command, without sudo or any parameters, to see if the configuration took place.
(I think I confused you a bit, excuse me...)
So, does

ifconfig

show you any proper IP-adress (right after doing the sudo ifconfig 192... stuff from above)?
If so, can you ping your router by it`s IP? (ping 192.168.???.???).
If network still doesn't work try the dhcp approach
(enable dhcp on the router and then
sudo dhclient eth0
then there should be DHCPOFFER)
and please report any error encountered

---

### Post by aran384 on 2006-08-29
this is the results of what you requested whizbaby:

aran384@ARAN001:~$ sudo ifconfig eth0 192.168.0.100 up
Password:
aran384@ARAN001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:A7:19:28
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fea7:1928/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:83615 (81.6 KiB)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5056 (4.9 KiB)  TX bytes:5056 (4.9 KiB)

aran384@ARAN001:~$

---

### Post by encompass on 2006-08-30
no longer needed....

---

### Post by whizbaby on 2006-08-30
So you got your desired IP, this means your network is running. Can you ping your router (ping routersIPaddress)? 
If yes, still no Internet ('ping www.google.com')? Then either configure the router back as dhcp-server and run 'sudo dhclient eth0' (posting errors) or have a closer look at the manual of your router to configure the static routing properly. Does your plugging look like this

computer --------> router ---------> DSL provider ---------> Internet ??

Does your router have an always-open connection to your provider, or how does it connect?
(and be sure that eth0 is the card you think)

---

### Post by aran384 on 2006-08-30
i still do not have a internet connection or connection to the network... 

:confused: 

am starting to think on getting rid of linux or changing to a different distro but i dont want to because i like ubuntu...! 

so am sorta kinda stuck now on what i should do... :(

---

### Post by whizbaby on 2006-08-30
No debugging information, no help.

---

### Post by aran384 on 2006-08-30
> **whizbaby said:**
> No debugging information, no help.

Am sorry but ur making me go in circles here... your asking me to do the same things that other people have asked me to do...

---

### Post by whizbaby on 2006-08-30
> **aran384 said:**
> Am sorry but ur making me go in circles here... your asking me to do the same things that other people have asked me to do...
I'm not stupid and have read the whole thread before giving advice. You have the impression to move in circles because you don't know what you're doing (e.g. trying dhclient without the router configured to dhcp), so some things have to be done twice because the first try wasn't right!
If it's really the same, why do you have an IP address now (which you hadn't before when checking with ifconfig)?
Did you change back your /etc/network/interfaces at the same time you configured your router back to dhcp?
What does 'sudo ethtool eth0' say about the state of network?

still no answers to my questions...

---

### Post by aran384 on 2006-08-30
im now on the internet with ubuntu... i downloaded the least version of ubuntu the beta one .... Edgy Eft i think :D

---

### Post by whizbaby on 2006-08-30
That's a solution, too.
Next time you got a problem try to post a little more info from your own...
good luck!

---

