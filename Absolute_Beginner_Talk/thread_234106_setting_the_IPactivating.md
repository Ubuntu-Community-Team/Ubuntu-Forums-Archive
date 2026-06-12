---
title: "setting the IP/activating"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by John Stoner on 2006-08-11
So, I'm setting a sstatic IP for my home LAN fileserver/mediaserver. I've updated /etc/networks/interfaces and /etc/resolv.conf files. When I issue ifconfig, it still says my old IP, so I try ifdown/ifup to restart the interface. 
 
ifdown fails, claiming that postfix can't find the main.cf file.

It takes down l0, but not eth0. 

two questions:

how do I get it to work, and

whose lamebrained idea was it to introduce a dependency on postfix in ifdown? I think postfix got installed with slimserver, for some reason.

---

### Post by John Stoner on 2006-08-16
In case anyone was wondering: configuring postfix (writing up a main.cf file) made this problem go away... not that it made all my problems go away (see other threads), but this one did.

---

### Post by vayde on 2006-08-19
I have the same problem.  In my case I believe postfix was installed with mysql, though I'm not sure why.

I get the postfix error all the time when interfaces come up, but it doesn't seem to hurt anything.

Occasionally the connection to the internet through the router won't come up, and then I see the error, but again I don't think that's what the problem is, as even when the connection comes up normally, the following:

ifup -v eth1 

shows the same error.

Will update if I find the problem.

---

