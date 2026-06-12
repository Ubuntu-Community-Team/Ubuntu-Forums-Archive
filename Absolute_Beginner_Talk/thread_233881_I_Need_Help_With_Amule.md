---
title: "I Need Help With Amule"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by NanoXstatiC on 2006-08-10
I can't seem to make Amule connect. I am totally at a loss, as I am a new Ubuntu user as of today. If anyone would be willing to walk me through the use of Amule in very simplistic terms, it would be greatly appreciated.

---

### Post by mlind on 2006-08-10
If you you have firewall or router, make sure that ports 4662 and 4672 are not blocked if you use the default settings.

---

### Post by NanoXstatiC on 2006-08-10
How exactly do I do that?

---

### Post by mlind on 2006-08-10
> **NanoXstatiC said:**
> How exactly do I do that?

It depends. Are you using firestarter or any other iptables front-end, or do you have hardware firewall/router?
If you don't use iptables or hardware firewall/router then you don't need to do this step.

When you have amule running, you should be able to connect port 4662 and 4672 using telnet
```

telnet localhost 4662

```

---

### Post by NanoXstatiC on 2006-08-10
I have a linksys wireless G router. It goes Modem>Router>PC. I am not using wireless personally.

As best i can tell, I am not using any sort of firewall or activity inhibiting software.

---

### Post by mlind on 2006-08-10
> **NanoXstatiC said:**
> I have a linksys wireless G router. It goes Modem>Router>PC. I am not using wireless personally.

As best i can tell, I am not using any sort of firewall or activity inhibiting software.

Do you get connection to ports 4462 and 4672 using telnet while amule is running? 
You can check the default ports from amule settings, Preferences > Connection.

---

### Post by NanoXstatiC on 2006-08-10
"no valid servers to connect to in serverlist"

What now? 

P.S. I have no idea how to test the ports...

---

### Post by mlind on 2006-08-10
> **NanoXstatiC said:**
> "no valid servers to connect to in serverlist"

What now?


Download a server list. Use google to search "emule server.met", find a working link and provide that for amule to download a server list

> **NanoXstatiC said:**
> 
P.S. I have no idea how to test the ports...

Use that telnet command I posted on reply [#4]("http://www.ubuntuforums.org/showpost.php?p=1364735&postcount=4")

---

### Post by Speedoo on 2007-07-16
I'm having the same problem.  I downloaded "server.met", but have no idea how to use it.  When I gedit it, it's an empty file.  How do I find a server for amule to get started?  Thanks!

---

### Post by Totentanz on 2007-07-16
Ok, i have similar problem.My TCP port connects normaly (4662) but my UDP port wont connect (4672).How to open that port?

---

### Post by Hallvor on 2007-07-16
[http://www.amule.org/wiki/index.php/Getting_Started](http://www.amule.org/wiki/index.php/Getting_Started)

---

### Post by amandalia47 on 2008-03-30
I am also having a problem with aMule.  I have correctly forwarded ports 4662 TCP, 4672 UDP, and 4665 UDP, and I am currently sharing all 9 GB of my music and I am still Firewalled.  I have tried disabling port forwarding on UDP port 4672 as mentioned in the Wiki FAQ, but I was still firewalled, I do not know if my router does NAT or not.  My globe icon shows a green Up arrow and a yellow Down arrow.  What more can I do?  

I am very new to Ubuntu so I'm terribly sorry if this is an obvious problem that I could just not figure out.

Thanks

---

### Post by stefangr1 on 2008-03-30
Not all emule server lists work in amule.

If you can't connect to a server, try the list from the following url:

[http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)

---

### Post by Hallvor on 2008-03-30
> **amandalia47 said:**
> I am also having a problem with aMule.  I have correctly forwarded ports 4662 TCP, 4672 UDP, and 4665 UDP, and I am currently sharing all 9 GB of my music and I am still Firewalled.  I have tried disabling port forwarding on UDP port 4672 as mentioned in the Wiki FAQ, but I was still firewalled, I do not know if my router does NAT or not.  My globe icon shows a green Up arrow and a yellow Down arrow.  What more can I do?  

I am very new to Ubuntu so I'm terribly sorry if this is an obvious problem that I could just not figure out.

Thanks

If the left arrow is green you are fine and not firewalled. KAD just needs more sources to bootstrap properly. You can solve this by downloading a popular file.

---

