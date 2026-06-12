---
title: "Problems connecting to the net... Ethernet"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by unconquerable on 2005-05-16
I am having problems connecting to the internet via ethernet and my Actiontec DSL gateway.  I did not have the computer configure itself during the Install of Ubuntu.  I have set DHCP on under Network Controls in Ubuntu and clicked the activate button.  My gateway is setup to automatically assign IP numbers for the computers connected to it.  The internet works for my mothers dell and my ibook.  

When I unplug the dell and plug the ethernet cable into the ubuntu machine I cannot access the internet, but I can access my gateway to configure it so I know the ethernet card works.

What do I do?

By the way I am a complete newbie with Linux.

I have also tried restarting with the ethernet plugged in.

---

### Post by wvslkr on 2005-05-16
[QUOTE=unconquerable]I am having problems connecting to the internet via ethernet and my Actiontec DSL gateway.  I did not have the computer configure itself during the Install of Ubuntu.  I have set DHCP on under Network Controls in Ubuntu and clicked the activate button.  My gateway is setup to automatically assign IP numbers for the computers connected to it.  The internet works for my mothers dell and my ibook.  

When I unplug the dell and plug the ethernet cable into the ubuntu machine I cannot access the internet, but I can access my gateway to configure it so I know the ethernet card works.

What do I do?

By the way I am a complete newbie with Linux.

I have also tried restarting with the ethernet plugged in.[/QUOTE]


Am I understanding correctly that you can contact the router from ubuntu?  If that
is the case it is most likely something in your dns setting.

In my case it is set to the router address.

---

### Post by unconquerable on 2005-05-16
Yes, I can connect to the router.  

Still not getting anything, I know the ethernet card works as this Box had suse on it previously.  Should I just reinstall?  ](*,)

---

### Post by unconquerable on 2005-05-17
UPDATE:

I Reinstalled Ubuntu with the ethernet cable hooked up.  I got through the whole process again without a hitch.   I went to start up the web browser and typed in [http://www.ubuntu.com](http://www.ubuntu.com), and held my breath.  :-# 

Then the title bar said Ubuntu - Linux for Human Beings
 I started to dance  \\:D/ 

Then it just kept loading.  Forever.  

Tried another page [http://www.cnn.com](http://www.cnn.com), no luck not even the title bar.  Now I can get nothing.  What the heck is going on?  ](*,)  :mad:  ](*,)

---

### Post by wvslkr on 2005-05-17
What nic do you have? Open a terminal and type  ifconfig  and post results.

---

### Post by unconquerable on 2005-05-17
> eth0 link encap:Ethernet HWaddr00:0d:88:39:B8:23
inet addr: 192.168.0.6  Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr:fe80::20d:88ff:fe39:b823/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU.1500 MEtric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3017  (2.9 KiB)  TX bytes:2016 (1.9 KiB)
Interrupt:11 Base address:0xe800

there is another part that starts with "lo" but isn't that something else?  I am sorry it is a pain in the butt as I must switch the monitor back and forth to copy this from one puter to another.

> lo  Link encap:Local Loopback
Inet addr:127.0.0.1 Mask:255.0.0.0
Inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:171 errors:0 dropped:0 overruns:0 frame:0
TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:14348 (14.0 KiB)  TX bytes:14348 (14.0 KiB)

I have a D-Link NIC

---

### Post by wvslkr on 2005-05-17
It appears your card is up ok. Try ping -c4 192.168.0.6 in term.

Then ping -c4 [www.yahoo.com](www.yahoo.com) and tell me what you get.

---

### Post by unconquerable on 2005-05-17
From 192.168.0.6
> 64 bytes from 192.168.06: icmp_seq=1 ttl=64 time=0.052
64 bytes from 192.168.06: icmp_seq=2 ttl=64 time=0.041
64 bytes from 192.168.06: icmp_seq=3 ttl=64 time=0.043
64 bytes from 192.168.06: icmp_seq=4 ttl=64 time=0.042

[www.yahoo.com](www.yahoo.com)
> 
64 bytes from yahoo.com (68.142.197.66): icmp_seq=1 ttl=53 time=64.7
64 bytes from yahoo.com (68.142.197.66): icmp_seq=2 ttl=53 time=64.1
64 bytes from yahoo.com (68.142.197.66): icmp_seq=3 ttl=53 time=63.1
64 bytes from yahoo.com (68.142.197.66): icmp_seq=4 ttl=53 time=63.3

---

### Post by wvslkr on 2005-05-17
You are getting out and getting an answer. What browser are you using?
Try another or have you allready?

---

### Post by unconquerable on 2005-05-17
Using firefox that comes with it.  No other browser on that machine.

---

### Post by unconquerable on 2005-05-17
Hell Yes!!!   \\:D/    :grin:  :grin:  :grin: 

I am writting this from ubuntu as we speak.  It wouldent load yahoo.com and then it did.  I tried a bunch of other sites and all I could get was the title bars, but I tried the forums and it went.  

 I don't understand why it is so sparadic.

THANKS for the help though any ideas on the weirdness?

---

### Post by unconquerable on 2005-05-17
Another Update:  The connection is being finicky as hell, it will load some pages and then the SAME page will not load at all when tried again.

---

### Post by wvslkr on 2005-05-17
I can't think of anything at the moment other than uninstalling Firefox and re-installing it.  I believe Epiphany is also in synaptic. Maybe try it.  I'll try to think 
of anything else.  Got to call it a night for now.  Back at you later. :)

---

### Post by unconquerable on 2005-05-17
My connecting is still cracked out.  It will connect to websites off and on at will.  I will get 5 minutes where I can connect and then a while where I cannot.

It does this for both when pinging a website and when using it through firefox, one second I will be able to ping/visit a site and the next I will not.  Could it be the router?  It always works with my mac and windows.  Isn't ethernet ethernet and it doesn't matte once it comes out of the router to the box, if it works on one it should on another?

 ](*,)

---

### Post by unconquerable on 2005-05-18
I found A driver for linux for the card I have, Yet I have no idea how to compile/install it any help?

[ftp://ftp.dlink.com/NIC/dfe530tx+/Driver/Linux/RTL8139.C](ftp://ftp.dlink.com/NIC/dfe530tx+/Driver/Linux/RTL8139.C)

---

### Post by wvslkr on 2005-05-18
I suspect that is probably the module in use.  You can run in term lsmod and
get a list of loaded modules.  Check that it should be r8139 I think. From 
what you have said I tend to believe something with the router or dns is the
culprit.  I have a different setup westell router on verizon and it will crash or hang 
occasionally.Overall very rare though.
When you get the time check your settings System>NetworkSettings>DNS
and lets have a look. Is it possible you Isp is having problems?  It has been a little flakey here today.

Have to go tonight hang in we'll figure it out yet.

---

### Post by UbuWu on 2005-05-18
Try this: [http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

---

### Post by nucrebain on 2007-02-03
Awww, I loath it when forums end abruplty with no solutions. :(

---

