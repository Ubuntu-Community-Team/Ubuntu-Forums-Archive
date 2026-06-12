---
title: "Old Pentium II 233 MMX with Ubuntu Server?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Jnetty99 on 2008-03-13
Friend gave me old system. Pentium II 233 MMX with 128mb RAM. Could this system run Ubuntu Server and then use the system as a file server? 

I been looking on craigslist for a small cheap dell system with more power but so far nothing good local. 

I been playing with VMware and would like to finally test things on an actual system.

edit:
I could get my hands on a Pentium II 333 processor at work instead if it makes things better.

---

### Post by SpaceTeddy on 2008-03-13
i don't know the requirement for an ubuntu server, but i have run four differnt installs of debian sarge and etch on old PII-200 Mhz with memory between 96 and 256 Mbyte of ram. They are slow - oh yes they are very slow, but they work nonetheless. The only thing you should never do on such a system (or so i think) is use a graphical system. But then i almost always stay in the CLI, so it is not a real change to me anyway. 

As for an answer - i don't know if it will work, but you can just give it a shot and see how it works out. As for what i did with my PII - one is still running as an internet gateway for about 200 students at a uni, one was a vpn server (replaced now), one was a vpn bridge (also replaced) and one was hosting a nagios server with about 150 services, which also got moved to a newer machine by now. They all handled their tasks quite well, tho.
I also had a K6-300 running as a home server for a while doing various things like samba, dhcp, ftp, apache, ssh, cvs, svn and a few more, and that worked quite well also. i only replaced it because at some point the cpu got fried from a power-surge.
I must stress, tho, all of them were debian servers (not ubuntu - but then ubuntu is based on debian) and none of them ever had a graphical system - CLI only !

hope it helps :)

---

### Post by jflaker on 2008-03-13
> **Jnetty99 said:**
> I could get my hands on a Pentium II 333 processor at work instead if it makes things better.

Keep talking to the IT guys at work and any other place which uses technology.  As their machines age or become unbootable due to a system error (not hardware related)....they often are replaced. 

The old systems usually end up in storage as it is difficult to give them away and it costs to recycle them..........

I have systems which I had gotten from my company which each had some kind of hardware problem.......from which I was able to piece together 3 working systems.  One I had given to my parents with Ubuntu............... Put the word out as you can probably get the systems for the cost of bringing them to your car.

Keep an eye out especially for rack boxes......these get old and don't support additional storage and are also put to storage.

---

### Post by Jnetty99 on 2008-03-13
SpaceTeddy

Thank you for your comments. I guess it doesnt hurt to try. Maybe i'll try older version of Ubuntu Server 6. 

jflaker
Me and the IT guy at work get along well, but unfortunately the processor he could give me, is the one type that would fit the motherboard i have. I used to have so many spare parts before and I gave them away.

---

### Post by PinkFloyd102489 on 2008-03-13
Im running server on a 300Mhz PII with 160MB RAM. Runs faster than my desktop, which is a PIII 450Mhz with 440MB RAM.

---

### Post by Jnetty99 on 2008-03-14
I got lucky. Found a Pentium 2.2hz Dell machine on craigslist for $50. Picking it up today. 
That system should do the trick.

---

### Post by the-edmeister on 2008-03-15
Pentium (I) 100MHz w/64MB RAM - an old Compaq 4132 - file server
4 HDDs totalling 600Gb - Staples clearance table last summer @ ~ $27 each
running on NASLite from a floppy disk
[http://www.serverelements.com/naslite.php](http://www.serverelements.com/naslite.php)

---

