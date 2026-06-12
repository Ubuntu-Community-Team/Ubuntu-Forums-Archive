---
title: "How can I tell if I am secure"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by margaf77 on 2007-07-23
Im behind a router and a grc scan shows me as stealthed but I ran nmap from my pc and below is the output.

I have firestarter and have a restrictive policy on outbound traffic and the inbound traffic with no ips in the list. 

I see port 25 open and from what I have read that is postfix, does that need to be installed if I dont have any mail server set up. I do have some shares set up for a windows pc to access set up here too. Am I secure or is there something I can do to secure myself more? Do I need those ports opened in order to function and if not how can I close them off?


```
kdesu -n /usr/bin/nmap -T Polite --allports -O -sT -v 192.168.0.101 > /tmp/kde-sf100/knmap_stderr_446680459 2> /tmp/kde-sf100/knmap_stderr_1979940042 

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-23 17:04 EDT
Initiating Parallel DNS resolution of 1 host. at 17:04
Completed Parallel DNS resolution of 1 host. at 17:04, 0.02s elapsed
Initiating Connect() Scan at 17:04
Scanning 192.168.0.101 [1697 ports]
Discovered open port 25/tcp on 192.168.0.101
Discovered open port 139/tcp on 192.168.0.101
Connect() Scan Timing: About 4.33% done; ETC: 17:16 (0:11:06 remaining)
Discovered open port 445/tcp on 192.168.0.101
Discovered open port 609/tcp on 192.168.0.101
Discovered open port 901/tcp on 192.168.0.101
Discovered open port 2049/tcp on 192.168.0.101
Discovered open port 111/tcp on 192.168.0.101
Completed Connect() Scan at 17:16, 691.26s elapsed (1697 total ports)
Initiating OS detection (try #1) against 192.168.0.101
Retrying OS detection (try #2) against 192.168.0.101
Initiating gen1 OS Detection against 192.168.0.101 at 708.224s
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
Host 192.168.0.101 appears to be up ... good.
Interesting ports on 192.168.0.101:
Not shown: 1690 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
609/tcp  open  npmp-trap
901/tcp  open  samba-swat
2049/tcp open  nfs
Device type: general purpose|broadband router|WAP|load balancer|storage-misc
Running (JUST GUESSING) : Linux 2.6.X|2.4.X (99%), Linksys embedded (92%), Siemens linux (91%), Kemp embedded (91%), Infrant RAIDiator (89%), Linksys Linux 2.4.X (89%), Asus Linux 2.4.X (89%), Maxtor Linux 2.4.X (89%)
Aggressive OS guesses: Centos 4.3 Linux 2.6.17.11-grsec (Centos 4.3, X86) (99%), Linux 2.6.15-27 (Ubuntu 6.06) (95%), Linux 2.6.14-gentoo-r2 (Gentoo, x86) (93%), Linksys WRT54GS v4 running OpenWrt w/Linux kernel 2.4.30 (92%), Siemens Gigaset SE515dsl wireless broadband router (91%), KEMP Technologies LoadMaster 1500 load balancer (91%), Linux 2.6.17 - 2.6.18 (91%), Linux 2.6.17.4 x86 Debian GNU/Linux 3.1 sarge (91%), Linux 2.4.18-10 (Red Hat 7.3) (90%), Linux 2.6.13 - 2.6.18 (90%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=0 (Trivial joke)
IPID Sequence Generation: All zeros

OS detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 739.216 seconds
               Raw packets sent: 83 (6700B) | Rcvd: 184 (11.532KB)

```

---

### Post by ReaderRat on 2007-07-23
This is what I found on firewalls:

[[color=red]Firewalls][/color]](http://www.linux.com/articles/55319?tid=13&tid=35)

---

### Post by scrooge_74 on 2007-07-23
Do this test [http://www.auditmypc.com/](http://www.auditmypc.com/)

---

### Post by margaf77 on 2007-07-23
OK, Without the firewall I had some open ports, 901 and 25. a bunch of closed ports and some stealthed. With it I was stealthed, as well as with my router.

I removed postfix figuring it is only necessary if I was running a mail server. Am I correct in this assumption?

---

