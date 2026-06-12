---
title: "Unable to access internet"
date: 2007-05-13
forum: California Team - US
---

### Post by baldwinian on 2007-05-13
I have Edgy Eft running on an old Dell. I have managed to get the wireless network card from Linksys to detect signals from my router. When I do iwlist I see my wireless network. 

When I try to access internet using Firefox I cannot connect.

Any thoughts?
Thanks
Kishen

---

### Post by madmetal on 2007-05-15
> **baldwinian said:**
> I have Edgy Eft running on an old Dell. I have managed to get the wireless network card from Linksys to detect signals from my router. When I do iwlist I see my wireless network. 

When I try to access internet using Firefox I cannot connect.

Any thoughts?
Thanks
Kishen

check on your laptop for DNS settings and at your router for wireless settings.. if there are any rules for access or block content..
Does Network manager say you are connected to wireless network?

UAResolved.

---

### Post by langyaw on 2009-06-29
> **madmetal said:**
> check on your laptop for DNS settings and at your router for wireless settings.. if there are any rules for access or block content..
Does Network manager say you are connected to wireless network?

UAResolved.

I am a complete idiot with Ubuntu.:( can you please give me  step-by-step instructions in working with Network Manager so I can connect to our Linksys broadband router?

---

### Post by Yasumoto on 2009-06-30
Open up a terminal, enter in these commands, and paste the output back to us:

uname -a

cat /etc/lsb-release

ifconfig

iwlist scan

---

### Post by langyaw on 2009-07-08
> **Yasumoto said:**
> Open up a terminal, enter in these commands, and paste the output back to us:

uname -a

cat /etc/lsb-release

ifconfig

iwlist scan

I'm typing the terminal's response since I don't know how to switch from Ubuntu to Windows without rebooting to be able to copy and paste. I hope I'd made no mistakes in typing them.
Below are the responses:
COMMAND: uname -a
REPLY: Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42 UTC 2008 i686 GNU/Linux
COMMAND: cat /etc/lsb-release
REPLY: DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
COMMAND: ifconfig
REPLY: eth0  Link encap:Ethernet HWaddr 00:1e:68:98:d3:d8
             UP BROADCAST MULTICAST  MTU: 1500 Metric:1
             RX packets:0 errors:0 dropped:2859463368 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
             Interrupt:218 Base address:0xe000
lo           Link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr: ::1/128  Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:486 errors:0 dropped:0 overruns:0 frame:0
             TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:30448 (30.4 KB) TX bytes:30448 (30.4 KB)
COMMAND: iwlist scan
REPLY: lo    Interface doesn't support scanning.
eth0         Interface doesn't support scanning.
pan0         Interface doesn't support scanning.

Now, what should I do? I'm excited to see Ubuntu being able to access the Internet, finally. I just might drop Window$ altogether. :popcorn:

---

### Post by Yasumoto on 2009-07-09
Would it be an option to upgrade to the newer (9.04) version of Ubuntu? Sorry to make you type everything out, but thanks for sticking with it. Maybe try burning a new Ubuntu 9.04 CD and see if you get internet while booting from that? Let me know if you don't want to upgrade, and we'll keep working on things.

---

### Post by langyaw on 2009-07-15
> **Yasumoto said:**
> Would it be an option to upgrade to the newer (9.04) version of Ubuntu? Sorry to make you type everything out, but thanks for sticking with it. Maybe try burning a new Ubuntu 9.04 CD and see if you get internet while booting from that? Let me know if you don't want to upgrade, and we'll keep working on things.

I'd just want to try out this version first, rather than going back to square 1. I'm worried about what a new install might do. Like I told you, I'm a freshie with Linux. I'd really appreciate the help. :) BTW, I've downloaded the Ubuntu guide for 8.10, but I can't find anything in it that will help me with my problem. it seems to assume that once Ubuntu is installed, it can immediately access the Internet. :(

---

### Post by langyaw on 2009-07-15
> **Yasumoto said:**
> Would it be an option to upgrade to the newer (9.04) version of Ubuntu? Sorry to make you type everything out, but thanks for sticking with it. Maybe try burning a new Ubuntu 9.04 CD and see if you get internet while booting from that? Let me know if you don't want to upgrade, and we'll keep working on things.

thanks, Yasumoto. I followed your advise, downloaded and installed 9.04 and in 2 clicks, I'm online! :guitar:

---

### Post by Yasumoto on 2009-07-15
Great news :)

Honestly, this might sound embarassing, but when I first started using Linux, I probably re-installed from scratch 10 times or so. It was usually just easier to have a separate /home partition, and be able to start over if I was playing around with stuff that didn't work.

Generally I'd say it's best to be running the latest stable release of Ubuntu, as that has the most polish/solid software running.

Be sure to post again if you have any other issues :)

---

