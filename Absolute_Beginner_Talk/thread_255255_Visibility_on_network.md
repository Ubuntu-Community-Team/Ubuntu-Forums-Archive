---
title: "Visibility on network"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by elpuerco on 2006-09-11
Is there some package etc I can use to test how 'visible' my laptop is on the network?

---

### Post by kidders on 2006-09-11
Hi there,

What do you mean by "visible" exactly? Are you interested in whether your computer is giving its presence away by scattering packets around the place, maybe?

For instance, even the "quietest" PC will perform the occasional DNS lookup or send queries to other devices, looking for (and providing) routing information.

Perhaps you're more interested in, say, WINS activity for example, that would tell you whether your PC is popping up in "network neighbourhood" style lists or not.

Feel free to clarify exactly what kind of visibility you're interested in, but in the meantime you might like to take a look at **ethereal** (or wireshark). It's a pretty common packet sniffer.

---

### Post by elpuerco on 2006-09-11
Well you might see from my other post that security is being disgusted by my friend and I and I am tying to clarify things for him and well for me to.

I have ZoneAlarms Pro when in WindowsXP and it says it 'hides' your IP address or whatever so you are not visible on the net.

Network security has never been my strong point which is why I was happy to have ZAP on WinXP as it was easy to use and I felt safe.

The lack of this kind of thing on Linux does make one ask the question though.

I did point out that I had read a lot that Linux is secure etc more so than Windows and so was looking for details

---

### Post by kidders on 2006-09-11
Ah, now I'm with you.

My understanding of the reason people use personal firewalls with Windows is that (a) they have no idea what kind of incoming connections their computers might decide to accept without asking for permission, and (b) Windows applications spend their lives phoning home constantly. If this sort of thing is what you're concerned about, then you'll be happy to know that, by and large, Linux is sensible, and won't turn itself into a spyware magnet if you take your eye off it for two seconds.

A number of firewalls are available for Linux (the most famous of which is perhaps iptables), that would let you exercise stricter control over what your computer does. It seems to me that your concerns are more to do with the internet than networks in general (which tend to behave completely differently).

**Edit:** Incidentally, anything that says it's hiding your IP address is lying.

---

### Post by elpuerco on 2006-09-12
Thanks, option a) was my concern :D

---

### Post by kidders on 2006-09-12
Ah. Forget about that one! Unless you explicitly instruct Ubuntu to listen for incoming connections, it won't. You can always check to satisfy yourself though ... use nmap to port sniff yourself :-)

---

### Post by elpuerco on 2006-09-12
oooo I shall try that sniffing of ports when I boot into Linux at home tonight, thnx =D>

---

### Post by kidders on 2006-09-12
Hehe 8-)

One thing I forgot to mention is that nmap may give you different results, depending on what interface (lo, eth0, eth1, etc.) you poke at with it. Be sure and sniff an interface that's externally accessible, so you know what other people are seeing when they try to break into you!

Also, you might find "netstat" useful. Among other things, it can list all current (and in the case of TCP, recent) network connections your computer is making.

Both utilities should already be on your Ubuntu box ... they're pretty standard issue for Linux!

---

### Post by elpuerco on 2006-09-12
Mmmm what to sniff?

How do I work this out?  

I have a ADSL Modem/Router which obviuosly does the connecting to the outside world and internally to this the router assigns dynamic IP address.

So which do I sniff?

---

### Post by kidders on 2006-09-13
Try using **nmap** to do a port scan of your external IP address. This will not always work from the "wrong" side of your DSL router, but if it's properly configured, you should be fine :-)

---

