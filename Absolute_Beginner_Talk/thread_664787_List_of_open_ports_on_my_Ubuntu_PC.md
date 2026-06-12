---
title: "List of open ports on my Ubuntu PC?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2008-01-11
Yeah I'm getting really really slow download speeds on BitTorrent and I've never had this problem before, maybe it has something to do with my ports I tell myself.

Testing some random port on Deluge (by using their own port tester) it says port XXX is closed. 

So here's my question: What ports are open as of right now on my PC, considering I've done NOTHING to open ANYTHING, everything is straight out of the box. 

I want to set a port that's already open and un-used for deluge. Thanks for the help. :)

---

### Post by Pevichaey5 on 2008-01-11
do you use a wireless connection to connect to the internet with a router? if so, that will block certain ports, but that won't affect your download speed

find out from you isp what the contention ratio is (one internet cable shared between how many houses)

hope that helps

---

### Post by papuccino1 on 2008-01-11
> **thexero said:**
> do you use a wireless connection to connect to the internet with a router? if so, that will block certain ports, but that won't affect your download speed

find out from you isp what the contention ratio is (one internet cable shared between how many houses)

hope that helps

IPS problems is a non issue, we don't bittorent throttling or throttling of any kind here in Bolivia. 

I use a wired connection. Not wireless, sorry for the mix up. 


So, there's no easy way for me to see what ports are open? That sucks...:(

---

### Post by Pevichaey5 on 2008-01-11
you can however, port scan your self by using nmap

its in the synaptic package manager

the go to [ip chicken](http://www.ipchicken.com) and the port scan that ip as it is your ip to other bit torrenters lol

---

### Post by papuccino1 on 2008-01-11
I don't understand the last bit. Clarification please? :(

---

### Post by Pevichaey5 on 2008-01-11
you need to find your ip address that you give to people who you download off with bit torrent

to find this address go to [ip chicken](http://www.ipchicken)

then use a program called nmap, which is what network administrators use for checking their security, and this will tell you what ports you have open and are not open

i recommend installing nmap fe with this though, it makes it alot easier to use

---

### Post by papuccino1 on 2008-01-11
Ok, I've done a scan using the IP given at IP Chicken.

Screenshot:
[IMG]http://i14.tinypic.com/8g3ypef.png[/IMG]


What ports are open? I can't make it out.

---

### Post by Clickbg on 2008-01-11
Every port is closed until some program open it for connections. If you did not touch your iptables then the problem is no in your pc, try to nmap your gateway. To test for specific port use -p option in nmap example: nmap myispip -p 80.

---

### Post by Pevichaey5 on 2008-01-11
i thought it was pretty obvious,

23
80
5190

thats the ports it says is open

it says 1694 ports are closed 

but on the right you only scanned the default ports, in the drop down, choose all and it will scan every single port on your computer

---

### Post by Rubruquis on 2008-01-11
Your 23, 80, 5190 TCP ports are open. You can always forward ports easily, so I'd suggest your to leave these ports on their own and forward a new port for torrent.

---

### Post by hangfire on 2008-01-11
Try **netstat -an**

-HF

---

### Post by papuccino1 on 2008-01-11
OK, I did this and it says all ports are closed. check it out.

Now the question is, how to I open these ports using a program? I don't have the admin password to my reuter and I can't get it from my ISP, they don't allow it.

[IMG]http://i10.tinypic.com/85fsk1z.png[/IMG]

---

### Post by (((X))) on 2008-01-13
ktorrent has a plugin to open ports on your system for faster downloads, not sure about other programs.

---

