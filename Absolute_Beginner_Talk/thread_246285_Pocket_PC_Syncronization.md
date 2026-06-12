---
title: "Pocket PC Syncronization"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by djshag on 2006-08-29
Hi! I was trying to install linux on my Pocket PC, but that seems to be a waste of time. So now I still need to sync it to my Ubuntu box. Installing SynCE worked up to the point where I get the "You have firewall rules that may prevent SynCE from working properly!" error.

From reading, I need to make sure that ports 5678, 5679 and 990 are opened to TCP connections over USB0. How do I do this?

Thanks!

BTW: These forums are great! A lot of knowledge around here....

---

### Post by lkh on 2006-08-29
Hi,

first tell us what kind of firewall you are running. The default package filter for Linux is iptables. You can install a good frontend for iptables named "firestarter". Otherwise you can use your own iptables script.

---

### Post by djshag on 2006-08-29
just checked Synaptic Package Manager and iptables is installed though I have no idea if it it default. I can only guess it is since I haven't installed one myself. Will check out firestarter. Thanks!

---

### Post by djshag on 2006-08-29
Hmmm... Firestarter does not see my USB device? What device am I concerned with... eth0 (ethernet), ra0 (wireless lan), sit0 (no idea what it is)?

---

### Post by djshag on 2006-08-30
Well, still no responses....

Anyway, may main problem is still ports. I keep getting:

> You have firewall rules that may prevent SynCE from working properly!


...and I cannot figure out how to open the proper ports!

Any help would be appreciated!

---

### Post by lkh on 2006-08-30
Hi,

I don't kbow what you have done. But by default iptables has no rules on a standard Ubuntu installation.

First you can try to flush all firewall rules (as root or with sudo):

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X
iptables -t nat -X
iptables -t mangle -X

Next you can try to remove the iptables module (as root or with sudo):

rmmod ip_tables
(if oyou can't remove this module try "lsmod | grep ip" and remove all modules used by ip_tables).

But I don't think you have a firewall problem ...

---

### Post by djshag on 2006-08-30
Well, messing with the iptables did not help sync the device, but I did lose internet connectivity. I'm using my MS computer right now as I have no idea how to reestablish the connection. Web browsers and email do not work but XMMS does.

BTW: I flushed the iptable settings but didn't remove the modules.

---

### Post by djshag on 2006-08-31
Anyone able to help me? I really do not wish to reinstall everything....

Thanks

---

### Post by lkh on 2006-08-31
Hi,

you need NAT or why you must use iptables for your internet connection? Tell us more how oyu connect to the internet.

With linux you do not have ro reinstall, reconfigure will be enough.

---

### Post by djshag on 2006-08-31
I connect through a wireless router. Had no problems up to about 36 hours ago when I was flushung the iptables settings. Since I really didn't do much else, I assumed that had to be the culprit. As I stated before, XMMS still connects and plays online radio streams, so I'm really screwed up now.

Oh wait, I did install Kubuntu and Xubuntu to check them out. Perhaps I should uninstall them. I did not use the apt-get method as the post I was reading said installing another way (I forgot the method) would be easier to remove later.

Could that have something to do with the web browser/ email client problem?

---

### Post by djshag on 2006-08-31
I connect through a wireless router. Had no problems up to about 36 hours ago when I was flushung the iptables settings. Since I really didn't do much else, I assumed that had to be the culprit. As I stated before, XMMS still connects and plays online radio streams, so I'm really screwed up now.

Oh wait, I did install the Kubuntu and Xubuntu desktops to check them out. Uninstalled them and it did not help.

Could that have had something to do with the web browser/ email client problem?

As for NAT through my router, I have that PC set up on a static IP address. When I run ifconfig, this is what I get:

> ra0   Link encap:Ethernet  HWaddr 00:10:A7:2E:A9:56
             inet addr:192.160.0.102 Bcast:192.168.0.255 Mask: 255.255.255.0
             inet6 addr:fe80::210:a7ff:fe2e:a956/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
             RX packets: 17860 errors:0 dropped:0 overruns:0 frame:0
             TX packets:192 errors:1736 dropped: 1736 overruns:0 carrier:0
             collisions:3 txqueuelen:1000
             RX bytes:6446589 (6.1MiB)  TX bytes:69531 (67.9) KiB
             Interrupt:5 Base address:0x8000
             

Had to type that all in by hand as my network is not working either. I just found that although I cannot connect to the internet via web browser, I can still connect to my router through it.

---

### Post by djshag on 2006-08-31
Add my router as DNS server to ra0 properties and that got internet access back. Don't know how that got screwed up, but at least that's now working.

---

### Post by djshag on 2006-08-31
Added my router as DNS server to ra0 properties and that got internet access back. Don't know how that got screwed up, but at least that's now working.

---

### Post by djshag on 2006-08-31
Added my router as DNS server to ra0 properties and that got internet access back. Don't know how that got screwed up, but at least that's now working.

---

### Post by djshag on 2006-08-31
Back to original problem: sync'ing my Toshiba e400 PDA. Seems like I'm talking to myself here a lot...

---

### Post by lkh on 2006-09-01
Hi,

pocket pc sync'ing is not what many of us do, so be patient.

I have read, that the message you posted can be ignored if you are sure not blocking this ports. I also don't really now what you hve done before. Best way to start with SynCE is this howto: [http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php).

Can you post the information of your device described in the chapter "Find out USB information about your device" of this hwoto?

---

