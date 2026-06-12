---
title: "Moblock working?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by cybertronix on 2007-12-25
Hey all

I've recently installed Ubunto and am trying to find my way around it!  I am a heavy Windows user so there's lots of things where Im going "HUH?" with!

One major HUH right now is with MOBLOCK (Peerguardian for linux).  I've installed it and performed a test as described here;  

[http://tutorialninjas.net/2007/10/10/protecting-your-linux-box-from-the-riaampaa/](http://tutorialninjas.net/2007/10/10/protecting-your-linux-box-from-the-riaampaa/)

# sudo moblock-control reload
# sudo moblock-control test

but the test result displays;


Trying to ping 4.2.145.239 from /etc/moblock/ipfilter.dat ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * 4.2.145.239 did not answer.
 * 
 * Maybe 4.2.145.239 is down/doesn't answer to pings
 * or your firewall filtered the ping.


I've installed Firestarter but disabled it and all, so I dont get it.

Also, isnt there a GUI for this program? something tangible, like Peerguardian?

and finally; I am wondering if I installed it correctly!

Thanks!!

---

### Post by markharding557 on 2007-12-25
moblock is crap,instead just put a blocking file directly in your software.
eg in amule or emule on wine you can install dat filters from here[http://www.bluetack.co.uk/forums/index.php]("http://www.bluetack.co.uk/forums/index.php")

---

### Post by harold4 on 2007-12-25
Pelle.K has a howto on the forum for moblock + firehol.  IMO, it's a great combo and works as expected.

For something GUI based, you can check out ipblocker, which is part of iplist.

markharding557: Why do you think moblock is crap?

---

### Post by markharding557 on 2007-12-26
> **harold4 said:**
> Pelle.K has a howto on the forum for moblock + firehol.  IMO, it's a great combo and works as expected.

For something GUI based, you can check out ipblocker, which is part of iplist.

markharding557: Why do you think moblock is crap?

found it to be unreliable and prone to going wrong for no apparent reason
iv'e found it much simpler to put a blocklist directly in the p2p app

---

### Post by cybertronix on 2007-12-26
> **markharding557 said:**
> moblock is crap,instead just put a blocking file directly in your software.
eg in amule or emule on wine you can install dat filters from here[http://www.bluetack.co.uk/forums/index.php]("http://www.bluetack.co.uk/forums/index.php")

Is it possible to do that with Bittorrent?

---

### Post by harold4 on 2007-12-26
ktorrent has a plugin for adding blocklists directly.

---

