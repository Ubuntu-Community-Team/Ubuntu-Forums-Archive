---
title: "URGENT!! internet connection sharing problem"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Dontspam on 2006-11-23
Hi!
I do not have much time so i'll get right to it:
few days ago I was happily sharing internet connection for my home lan without problems (I had mandrake linux). Then my hard drive gave up (being 8 years old it's not a surprise). The only thing I could to was to master my another drive which had ubuntu 6.06 installed. That is where the broblems started again:

I have NEVER been able to fully share the network with ubuntu. Some software like skype will get through from the lan, but no http whatsoever.
The lan clients (winXP) are unable to browse the internet ](*,) 

I have tried firestarter, tinyproxy, almost everything generally recognizable, but the result is much of the same: no http proxying, just skype and some other progs. This problem keeps being very annoying; mandrake got the network shared with ease (but mandrake itself was somewhat unstable), but ubuntu just can't, WHY???

Now, I'm in a tight spot: As I said the linux machine is supposed to act as a firewall for the lan as well as sharing the internet connection for lan clients. Now the lan clients don't have internet access, and folks are getting angry :( If someone can help me with this problem, please do so as quick as possible

---

### Post by rlozano on 2006-11-23
did you try, for trouble shooting purposes, without any firewall in your ubuntu machine?

---

### Post by squidward_tentacels on 2006-11-23
Without knowing your specific configuration, its only guesswork...However, I believe Ubuntu has IPv6 enabled by default; have you tried disabeling it? Just a thought.

---

### Post by Dontspam on 2006-11-23
My network configuration setup is following: 

[ADSL Modem] --> [DHCP >Ubuntu linux> static 192.168.0.1] --> [HUB/switch] --> [LAN clients (192.168.0.x)]

This configuration worked fine when Mandrake harddrive still worked... Mandrake used squid to do it I quess :neutral: Haven't been able to get squid working on ubuntu...

Yes, I have tried disabling IPv6 (if it is done in conf file by commenting the line that says something about IPv6 forwarding...)
How to disable it "properly" ? :confused: 

I have tried without firewall (ie. no firestarter, tms installed)
But firestarter is not a firewall, it is only a configuration prog. 
did you mean to disable kernel firewall? how is this done? :confused:

---

### Post by f76 on 2006-11-23
how about Internet>switch>Ubuntu. It works for me and is flexible and easy to configure.

---

### Post by Dontspam on 2006-11-23
Nope, that confiquration won't work for me
I need the LAN clients to have static IPs. The only way to do this (to my sense) is to have a router (ubuntu machine) between dhcp and static LAN

BESIDES: the question is: What is wrong with ubuntu? How does an old mandrake version manage to do things better than new ubuntu? why can't I do the same thing with ubuntu that I did with mandrake???
](*,)

---

### Post by f76 on 2006-11-23
Im sorry I cant answer why it is hard to do this on ubuntu - im no hacker anyway :). but what kind of switch do you have? -or is it just a hub?

---

### Post by Dontspam on 2006-11-23
My switch is... a standard 10/100 switch... there is nothing special about it as far as I know.
Besides, it worked fine with mandrake, why wouldn't it work with ubuntu (unless ubuntu is nothing but a big fraud with fancy cover). I wouldn't like revert to that old and crappy mandrake anymore... It had a log filling problem I weren't able to totally resolve.

So, any idea what could be wrong with my setup? I can post command lines I have used if it helps in any way...

---

### Post by FredSambo on 2006-11-23
FWIW, firestarter doesn't work with two NIC cards, only one at a time.

you should use IP cop (in a virtual machine perhaps) as a router/firewall for your LAN.

---

### Post by Dontspam on 2006-11-24
But the following configuration was the one that worked with mandrake+squid:

[ADSL modem] -> [DHCP > ubuntu > LAN 192.168.0.1] -> [switch] -> [LAN client PCs]

The ubuntu machine has two standard 10/100 networking cards eth0 and eth1
eth0 is configured with DHCP to connect the internet and eth1 has static IP and is connected to LAN through a switch.

I'd like to route the internet access THROUGH ubuntu machine into LAN, This was formerly done with mandrake+squid HTTP proxy (there is a package named "squid" for ubuntu, but I cannot get it isntalled ](*,) )
Why doesn't it work on ubuntu?
Why the network sharing isn't working with firestarter?
:confused: :confused: :confused:

---

### Post by mips on 2006-11-24
The way you current diagram looks things will NOT work.

Please post the following for me with BOTH ehternets connected.

**ifconfig -a**

Look at this example and pay carefull attention to the IP addressing !!!
[http://www.ubuntuforums.org/showthread.php?t=269235](http://www.ubuntuforums.org/showthread.php?t=269235)

The above example should have you up & running in no time, you are just going to have to configure more pc's instead of 1 xbox. You could also do DHCP if you want for the client PC's

[I]If you want something a bit more technical &  involved look here:
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)[/I]

---

### Post by Dontspam on 2006-11-24
Nope, it doesn't work...

The thing i'm wondering here is that the ubuntu machine actually shares the network for LAN... but only skype gets through from client machines.

the configuration is as follows:

ADSL modem
     |
ETH0 (DHCP) this is the first network card of the linux box
---Ubuntu box--- (former mandrake+squid http proxy)
ETH1 (192.168.0.1)
     |
HUB/switch
-Client PC 1, 192.168.0.2
-Client PC 2, 192.168.0.3
-etc...

This setup worked fine on mandrake, I cannot see how you imply it wouldn't work. NO, the problem lies within ubuntu, it must be...

This is what ifconfig told me:

eth0      Link encap:Ethernet  HWaddr 00:0C:46:17:55:B2
          inet addr:something  Bcast:anthr something        Mask:255.255.240.0
          inet6 addr: fe80::20c:46ff:fe17:55b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:52287345 (49.8 MiB)  TX bytes:127479105 (121.5 MiB)
          Interrupt:11 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:0E:2E:29:D4:78
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe29:d478/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:123931173 (118.1 MiB)  TX bytes:23314627 (22.2 MiB)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:235396 (229.8 KiB)  TX bytes:235396 (229.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I hope this is of some help...
Oh, and I can ping the LAN client machines from ubuntu machine, 0% packet loss

---

### Post by Dontspam on 2006-11-26
AND i'd like to get some response soon. The LAN internet access has been down for too many days (people getting angry)

---

### Post by Dontspam on 2006-11-30
...
Honestly now, anyone here who could help me? I've got a problem here!

---

### Post by Pionner on 2006-11-30
I used to have a similar network configuration. Firestarter didn't work for me, so I tried firewall-jay (it is not in the repos, but a .deb can be downloaded [form here]("http://osdn.dl.sourceforge.net/sourceforge/firewall-jay/firewall-jay_1.0.5-1_i386.deb")).

The configuration it's easy (ncurses based): identify the two network cards Internet / LAN, activate NAT and you're done.

I hope this helps.

---

