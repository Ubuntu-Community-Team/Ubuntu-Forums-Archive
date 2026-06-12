---
title: "Network problem with server install?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by teasum on 2006-04-02
I have some old hardware lying around, so I'm trying to make some use out of them by making a simple file server out of them.  I've found some howto's online, but I'm running into problems after I install the base system.  I can't seem to access the online repositories with apt-get.  

Basic system specs: Compaq DeskPro 4000 (I think), 200mHz Pentium Pro, 160mb RAM, onboard LAN

Here's what I've done so far: I ran the live CD to check the network connection, and it's fine through breezy live (though slow, of course!), and I browsed around to a couple websites.  Also, I'm in university housing where we have to register our devices on the network, which I did through firefox on the live CD.  However, if I boot into the base system I've installed, ifconfig doesn't show the eth0 connection at first.  After entering "ifconfig eth0 up" it does list the connection as up, but otherwise no activity.  "sudo apt-get update" simply returns a bunch of errors trying to access the online repositories.  I also double-checked my network registration with the university, and the MAC address that I registered through the live CD is the same as with the base system / server install, so no glitch there. 

This is all besides the many problems / questions I'll probably have trying to set this machine up as a server, but first things first--I need to actually connect to the repositories.

Any help is appreciated!

---

### Post by dcstar on 2006-04-02
[QUOTE=teasum]I have some old hardware lying around, so I'm trying to make some use out of them by making a simple file server out of them.  I've found some howto's online, but I'm running into problems after I install the base system.  I can't seem to access the online repositories with apt-get.  

Basic system specs: Compaq DeskPro 4000 (I think), 200mHz Pentium Pro, 160mb RAM, onboard LAN

Here's what I've done so far: I ran the live CD to check the network connection, and it's fine through breezy live (though slow, of course!), and I browsed around to a couple websites.  Also, I'm in university housing where we have to register our devices on the network, which I did through firefox on the live CD.  However, if I boot into the base system I've installed, ifconfig doesn't show the eth0 connection at first.  After entering "ifconfig eth0 up" it does list the connection as up, but otherwise no activity.  "sudo apt-get update" simply returns a bunch of errors trying to access the online repositories.  I also double-checked my network registration with the university, and the MAC address that I registered through the live CD is the same as with the base system / server install, so no glitch there. 

This is all besides the many problems / questions I'll probably have trying to set this machine up as a server, but first things first--I need to actually connect to the repositories.

Any help is appreciated![/QUOTE]

On the assumption you are connecting through a Proxy server, you need to set up Synaptic to use the Proxy server.

Do a forum search for posts with detailed solutions.

---

### Post by R3linquish3r on 2006-04-02
I may be thinking backwards, but your sources aren't uncommented (I'm guessing you just recently had Ubuntu installed). If that is the case you need to go to you /etc/apt/sources.list and uncomment the repositories.

---

### Post by teasum on 2006-04-03
Thanks for the feedback.

1) My sources are uncommented, this I can confirm.  Even before modifying /etc/apt/sources.list, there are two uncommented online repositories in there, and they aren't loading either.  But in any case I had uncommented them all before trying to connect.

2) I do not believe there is a proxy server I need to worry about, since every other computer I have simply connects with no cofiguring necessary, beyond the university-required registration process (which basically just registers the MAN address and OS of your hardware).  One question, however: would a proxy server be something automatically handled on a Breezy live CD, but not through a base system (i.e. server) installation?

Thanks!

---

### Post by teasum on 2006-04-03
[QUOTE=dcstar]On the assumption you are connecting through a Proxy server, you need to set up Synaptic to use the Proxy server.[/QUOTE]

One point of clarification.  I don't think I'm using Synaptic, since it's a base-system off a server install.  I'm only using apt-get.  Does this make a difference?

Another active thread seems to be about a similar problem, though not off a server install: [http://ubuntuforums.org/showthread.php?t=152856](http://ubuntuforums.org/showthread.php?t=152856).

Thanks!

---

### Post by teasum on 2006-04-05
Anybody out there have any advice?

To recap: I have a minimal base-system installed (server install--(no Gnome, no KDE, no xfce, no nothing... just CLI), and I can't access the online repositories.  My sources.list file is all uncommented (except for the CD, which is commented out).  If I try to ping something, I get a "Network is unreachable" error.  I'm pretty sure I'm not behind a proxy server, and a bunch of searching around my school's website, there's no info about proxy servers.  I can connect via the live CD with no problem.  

So, the question becomes: what do I need to do to connect to the net (and thus use apt-get) with my ubuntu base-system?

Help!

---

### Post by jamesr on 2006-04-05
Can you ping the DNS server in the university, then google.

---

### Post by teasum on 2006-04-05
[QUOTE=jamesr]Can you ping the DNS server in the university, then google.[/QUOTE]

Nope.  Any attempt to ping an IP address brings back the error: 
> connect: Network is unreachable

Any attempt to ping a website (i.e. [www.google.com](www.google.com)) brings back:
> ping: unknown host [www.google.com](www.google.com)

I think that for some reason my network connection is borked through the minimal install, though I don't know how or why.  Perhaps I'll just try to reinstall the whole thing again and see what happens, though I'm not optimistic.

---

### Post by jamesr on 2006-04-05
One of my systems is a server ie minimal installation and the network works well. It is used as my Archival Fileserver. Although I did setup it manually.
Please post the output of```
sudo ifconfig -a
dmesg | grep eth0
```

---

### Post by teasum on 2006-04-06
[QUOTE=jamesr]One of my systems is a server ie minimal installation and the network works well. It is used as my Archival Fileserver. Although I did setup it manually.
Please post the output of```
sudo ifconfig -a
dmesg | grep eth0
```[/QUOTE]

Here's my output:
sudo ifconfig -a:

> 
eth0	Link encap:Ethernet  HWaddr 00:80:5F:A1:C5:6A
	BROADCAST MULTICAST  MTU:1500  Metric:1
	RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
	Interrupt:11 Base address:0x1000

lo	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0b)  TX bytes:0 (0.0b)

Note that this is without manually activating eth0.  Of course, should I even have to activate the connection manually?

dmesg | grep eth0
> [   50.934660] TLAN: eth0 irq=11, io=1000, Compaq Integrated NetFlex-3/P, Rev.16

That's it.  Now what?

---

### Post by jamesr on 2006-04-07
> eth0 Link encap:Ethernet HWaddr 00:80:5F:A1:C5:6A
BROADCAST MULTICAST MTU:1500 Metric:1
shows that the card is at least seen although with no TCP/ip address
```
sudo dhclient eth0
``` should get the address as long the the DHCP is activated in the router

---

### Post by teasum on 2006-04-07
[QUOTE=jamesr]shows that the card is at least seen although with no TCP/ip address
```
sudo dhclient eth0
``` should get the address as long the the DHCP is activated in the router[/QUOTE]

That did the trick.  Thanks!  This sounds really simple... but should I be able to configure this to happen automatically on startup?

Anyhoo, thanks for the help!

---

