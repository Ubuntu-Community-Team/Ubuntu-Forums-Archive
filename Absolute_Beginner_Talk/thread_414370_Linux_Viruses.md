---
title: "Linux Viruses"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-04-19
The recent post on Linux malware (cafe forum) got me thinking.

I use Windows and I'm certainly paranoid about malware and regularly check my 'running processes', disk activity and startup entries for anything suspicious. I've even blocked iTunes from starting itself to keep system resources free.
Thankfully I've never actually had a Windows virus.

Linux on the otherhand is all very new to me and I'm a bit daunted by it's 'spread out' file structure. So if I did obtain a virus (or even some unnecessary software hogging my resources), how would I know before it's too late?

---

### Post by igknighted on 2007-04-19
use the command "top" in the terminal to see your active processes.  There is a system monitor GUI in the menu a well (system->admin->system monitor).

---

### Post by siciliancasanova on 2007-04-19
I have a system resource monitor running and use firestarter for my firewall.

Not really an answer to your question, but my answer for why I don't need to ask that question.

---

### Post by aktiwers on 2007-04-19
If you like "top" you can also install "htop" witch is almost the same, but a little cooler.
```
sudo apt-get install htop
```

---

### Post by eyelessfade on 2007-04-19
try chkrootkit.

chkrootkit - Checks for signs of rootkits on the local system

---

### Post by MikeBgts on 2007-04-19
The main concern, should be about rootkits. So eyelessfade advice is the best. You can also install clamav antivirus as an extra.

---

### Post by aktiwers on 2007-04-19
Hey I just installed and ran chkrootkit..  at the end of the scan it shows this?
> Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1:avahi: PACKET SNIFFER(/sbin/dhclient3[5232], /usr/sbin/avahi-autoipd[5218])
eth0: PACKET SNIFFER(/sbin/dhclient3[3909])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted
aktiwers@HAL:~$ 


??

Does this mean I have a packed sniffer?
eth1:avahi: PACKET SNIFFER(/sbin/dhclient3[5232], /usr/sbin/avahi-autoipd[5218])

??

---

### Post by Pobega on 2007-04-19
I recommend ClamAV for virus scanning. aegis-virus-scanner is nice too, and all-in-all is easier to use, but most of the time ClamAV picks up viruses AVS missed (Windows viruses though, I've never had a "Linux virus")

---

### Post by jasonbrisbane on 2007-04-19
Hope I'm giving the right advise here...

Dont network cards have to be "Packet Sniffers" so they can monitor for requests from other computers for network info and other Network related info (ie Packets?)?

---

### Post by phen on 2007-04-21
avahi is afaik **supposed** to "sniff" packets, and dhclient too. don't worry. there is virtually no virus thread under linux. using it for 10 years now, never had problems.... (never installed anything like a virus scanner or firewall whatsoever)

there is for sure something written in the ubuntu wiki regarding security: wiki.ubuntu.com or here,
[https://help.ubuntu.com/community/InstallingSecurityTools](https://help.ubuntu.com/community/InstallingSecurityTools)
if you're really paranoid. but many of these tools are hacker tools and also suited to attack (like kismet etc) and anyway more suited for network admins.

---

### Post by Sef on 2007-04-21
> (never installed anything like a virus scanner or firewall whatsoever)

The firewall is part of the kernel and runs all the time.  Firestarter is gui front end for [iptables]("http://en.wikipedia.org/wiki/Netfilter"), the firewall.

---

