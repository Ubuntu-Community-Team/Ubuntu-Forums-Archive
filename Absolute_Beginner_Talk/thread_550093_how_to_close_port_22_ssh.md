---
title: "how to close port 22 ssh"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-09-13
how do you close port 22 ssh. Gibson's shields up says it's wide open. Thanks in advance.Paul

---

### Post by csimons on 2007-09-13
The most common way to do this on GNU/Linux systems is to deny access to the daemon by using the hosts.deny file.  You could put the following in /etc/hosts.deny to effectively close the port:

sshd : ALL

This will deny access to the sshd daemon from all foreign hosts.  If you then, for example, wanted to allow access from other computers on your local network, you might put something like the following in your /etc/hosts.allow file:

sshd : 192.168.1.

This will allow access to the daemon from all computers in the 192.168.1.0 network.

For more information, try doing a "man hosts.allow" or a "man hosts.deny" from a terminal.

---

### Post by csimons on 2007-09-13
It seems someone had a similar question about a year ago:

[http://ubuntuforums.org/showthread.php?t=248342](http://ubuntuforums.org/showthread.php?t=248342)

---

### Post by asmoore82 on 2007-09-13
open "System -> Admisistration -> Services" and turn off the "Remote Shell Server"

...
if you don't need it at all you could just uninstall the 'openssh-server' package
the service/port are not available/open on Ubuntu "out of the box."

sshd with the lastest security updates in place is perfectly safe and quite usefull to leave open,
as long as you ONLY use ssh protocol 2, to check this ...
```
~$ grep Proto /etc/ssh/sshd_config
``` should simply say "Protocol 2"

sshd, IMO, is a quick and safer way to do filesharing, you can choose SSH as the
"Service type" in "Places -> Connect to server" and "mount" remote folders 100% encrypted.

---

### Post by psusi on 2007-09-13
Why would you want to close it?  You installed sshd so apparently you wanted it running.

---

### Post by pdlethbridge on 2007-09-13
1. remote shell server  -  not listed
2. openssh-server   -  not installed
3. grep Proto /etc/ssh/sshd_config  -   No such file or directory
 So after doing what you say, it appears I'm save from attack,,, or not..
I checked my XP partition and it showed the same problem. At this point, I really don't know what to think. I run firestarter in ubuntu 7.04 and zone alarm in XP
Changing routers didn't change a thing. Adding a linksys router between the computer and th cable modem/router didn't change anything. I'm almost thinking I may have another problem

---

### Post by pdlethbridge on 2007-09-13
This is what I get from shields up.

Solicited TCP Packets: RECEIVED (FAILED) — As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.



Unsolicited Packets: PASSED — No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)



Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.


Port	
Service 	
Status 	Security Implications

0 	
<nil> 	
Stealth 	There is NO EVIDENCE WHATSOEVER that a port (or even any computer) exists at this IP address!

21 	
FTP 	
Stealth 	There is NO EVIDENCE WHATSOEVER that a port (or even any computer) exists at this IP address!

22 	
SSH 	
OPEN! 	Secure Shell provides a secure-connection version of the Telnet remote console service with additional features. Unfortunately, the SSH services and their security add-on packages have a long history of many widely exploited buffer overflow vulnerabilities. If your system has this port exposed to the outside world you should be vigilant in keeping your SSH service updated.

---

### Post by reckless2k2 on 2007-09-13
wait...if you put a DIFFERENT router between the cable modem AND your PC and a shields up scan showed port 22 still open then there's an issue with the router having port 22 open. go into port forwarding and disable 22. i thought you were direct to cable modem.

---

### Post by pdlethbridge on 2007-09-13
I spent a half hour on the phone this morning with time warner and they can't close the port and there is no way for me to close it.

---

### Post by reckless2k2 on 2007-09-13
ok....SO...if no machine on your net has port 22 open then your fine. 22 has got to direct somewhere.......if no somewhere then nowhere it will go. 

TM might have it open so they can play with the modem if need be. so that's them to modem. done. not wlaking in your door and sitting down at your couch with feet up asking for a beer. 

get it?

i can have 80 open all day long to nothing. shieldsup will show open but to nowhere it'll go.

---

### Post by psusi on 2007-09-13
If you are connecting though a firewall, then it is the firewall that is running sshd, unless it is configured to forward that port or lists a computer in the DMZ.  

If you connect directly and it still shows you are listening on that port, check the output of netstat -a --tcp | grep LISTEN

---

### Post by psusi on 2007-09-13
> **reckless2k2 said:**
> ok....SO...if no machine on your net has port 22 open then your fine. 22 has got to direct somewhere.......if no somewhere then nowhere it will go. 

TM might have it open so they can play with the modem if need be. so that's them to modem. done. not wlaking in your door and sitting down at your couch with feet up asking for a beer. 

get it?

i can have 80 open all day long to nothing. shieldsup will show open but to nowhere it'll go.

If it goes nowhere then it isn't open.  Open means it goes to somewhere that picked up the line.

---

### Post by asmoore82 on 2007-09-13
scan the computer with nmap ...

```
~$ sudo apt-get install nmap
~$ sudo nmap -v -A localhost
```

and see what's really going on.

IF your router shows port 22 open but it isn't actually open on your computer that is a *good* thing.
That would mean that your router is intentionally *wasting* the time of jerks doing brute force scans.

---

### Post by pdlethbridge on 2007-09-14
this is what I got after running what you said:
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-13 23:58 EDT
Initiating SYN Stealth Scan at 23:58
Scanning localhost (127.0.0.1) [1697 ports]
Discovered open port 631/tcp on 127.0.0.1
Completed SYN Stealth Scan at 23:58, 0.09s elapsed (1697 total ports)
Initiating Service scan at 23:58
Scanning 1 service on localhost (127.0.0.1)
Completed Service scan at 23:59, 6.04s elapsed (1 service on 1 host)
Initiating OS detection (try #1) against localhost (127.0.0.1)
Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE VERSION
631/tcp open  ipp     CUPS 1.2
Device type: general purpose
Running: Linux 2.6.X
OS details: Centos 4.3 Linux 2.6.17.11-grsec (Centos 4.3, X86)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=194 (Good luck!)
IPID Sequence Generation: All zeros

OS and Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap finished: 1 IP address (1 host up) scanned in 7.528 seconds
               Raw packets sent: 1716 (76.266KB) | Rcvd: 3436 (145.376KB)

---

### Post by splintercellguy on 2007-09-14
Why nmap on the local loopback interface? Is it not better to do it from outside the network? But yes, it appears you don't have any SSH service open.

---

### Post by pdlethbridge on 2007-09-14
Interestingly, port 631 was hiddehin stealth at shields up. What does it all mean? I'm sooooo confused

---

### Post by pdlethbridge on 2007-09-14
the second time I ran the test I got this result.
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-14 04:38 EDT
Initiating SYN Stealth Scan at 04:38
Scanning localhost (127.0.0.1) [1697 ports]
Discovered open port 22/tcp on 127.0.0.1
Discovered open port 631/tcp on 127.0.0.1
Completed SYN Stealth Scan at 04:38, 0.11s elapsed (1697 total ports)
Initiating Service scan at 04:38
Scanning 2 services on localhost (127.0.0.1)
Completed Service scan at 04:38, 6.04s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against localhost (127.0.0.1)
Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 4.3p2 Debian 8ubuntu1 (protocol 2.0)
631/tcp open  ipp     CUPS 1.2
Device type: general purpose
Running: Linux 2.6.X
OS details: Centos 4.3 Linux 2.6.17.11-grsec (Centos 4.3, X86)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=203 (Good luck!)
IPID Sequence Generation: All zeros
Service Info: OS: Linux

OS and Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap finished: 1 IP address (1 host up) scanned in 7.621 seconds
               Raw packets sent: 1716 (76.266KB) | Rcvd: 3437 (145.420KB)
pdleth@pdleth-desktop:~$

---

### Post by psusi on 2007-09-14
Yea... you installed openssh.... ok?

---

### Post by pdlethbridge on 2007-10-09
installing denyhosts from synaptic and see how that works.

---

