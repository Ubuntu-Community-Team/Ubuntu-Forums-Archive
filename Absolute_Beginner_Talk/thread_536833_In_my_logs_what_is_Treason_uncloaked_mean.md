---
title: "In my logs what is Treason uncloaked mean??"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-28
Hi,

what does this mean?

```
Aug 28 13:16:32 lotus kernel: [61238.407346] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238402976:2238405685. Repaired.
Aug 28 13:16:34 lotus kernel: [61240.654268] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238402976:2238405685. Repaired.
Aug 28 13:16:38 lotus kernel: [61245.148114] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238402976:2238405685. Repaired.
Aug 28 13:16:56 lotus kernel: [61262.715792] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238426208:2238430369. Repaired.
Aug 28 13:16:58 lotus kernel: [61264.690855] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238426208:2238430369. Repaired.
Aug 28 13:17:02 lotus kernel: [61268.640984] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238426208:2238430369. Repaired.
Aug 28 13:17:10 lotus kernel: [61276.541244] TCP: Treason uncloaked! Peer 80.128.87.225:2861/4662 shrinks window 2238426208:2238430369. Repaired.
Aug 28 14:26:22 lotus kernel: [65427.139346] TCP: Treason uncloaked! Peer 80.128.87.225:21/2087 shrinks window 2372454999:2372459944. Repaired.
Aug 28 14:26:24 lotus kernel: [65428.810552] TCP: Treason uncloaked! Peer 80.128.87.225:21/2087 shrinks window 2372454999:2372459944. Repaired.
Aug 28 14:26:27 lotus kernel: [65432.152982] TCP: Treason uncloaked! Peer 80.128.87.225:21/2087 shrinks window 2372454999:2372459944. Repaired.
Aug 28 14:26:34 lotus kernel: [65438.837809] TCP: Treason uncloaked! Peer 80.128.87.225:21/2087 shrinks window 2372454999:2372459944. Repaired.
Aug 28 14:26:47 lotus kernel: [65452.207454] TCP: Treason uncloaked! Peer 80.128.87.225:21/2087 shrinks window 2372454999:2372459944. Repaired.
Aug 28 14:57:41 lotus kernel: [67305.535871] TCP: Treason uncloaked! Peer 80.128.87.225:21/4825 shrinks window 103623225:103626564. Repaired.
Aug 28 14:57:43 lotus kernel: [67307.263033] TCP: Treason uncloaked! Peer 80.128.87.225:21/4825 shrinks window 103623225:103626564. Repaired.
Aug 28 14:57:47 lotus kernel: [67310.717401] TCP: Treason uncloaked! Peer 80.128.87.225:21/4825 shrinks window 103623225:103626564. Repaired.
Aug 28 14:57:54 lotus kernel: [67317.626142] TCP: Treason uncloaked! Peer 80.128.87.225:21/4825 shrinks window 103623225:103626564. Repaired.
Aug 28 14:58:07 lotus kernel: [67331.443577] TCP: Treason uncloaked! Peer 80.128.87.225:21/4825 shrinks window 103623225:103626564. Repaired.
Aug 28 20:05:25 lotus kernel: [85761.268766] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403579163:2403582948. Repaired.
Aug 28 20:05:28 lotus kernel: [85763.819551] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403579163:2403582948. Repaired.
Aug 28 20:05:45 lotus kernel: [85779.616115] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403638963:2403641548. Repaired.
Aug 28 20:05:46 lotus kernel: [85782.278805] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403638963:2403641548. Repaired.
Aug 28 20:05:51 lotus kernel: [85787.604284] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403638963:2403641548. Repaired.
Aug 28 20:06:02 lotus kernel: [85798.255216] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403638963:2403641548. Repaired.
Aug 28 20:06:23 lotus kernel: [85819.557118] TCP: Treason uncloaked! Peer 80.128.87.225:21/2147 shrinks window 2403638963:2403641548. Repaired.
```

thanks..

---

### Post by asmoore82 on 2007-08-28
from linuxquestions.org ...
[QUOTE="chort"]In any case, the short answer is that it looks like someone is spoofing an IP, feigning a connection to your http and pop3 servers, then setting their window size to 0 so your daemon sits there trying to send them the data over and over (for instance, they may start a connection and immediately set their window to 0, so you cannot send back the http or pop3 connection banner message).
...[/QUOTE]

my own investigation into this IP address that is attacking you yeilded these results:
```
**asmoore@eddy:~$** nmap -v **80.128.87.225**

Starting Nmap 4.20 ( http://insecure.org ) at 2007-08-28 08:47 EDT
Note: **Host seems down. If it is really up, but blocking our ping probes**, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.004 seconds
**asmoore@eddy:~$** nmap -v -P0 **80.128.87.225**

Starting Nmap 4.20 ( http://insecure.org ) at 2007-08-28 08:47 EDT
Initiating Parallel DNS resolution of 1 host. at 08:47
Completed Parallel DNS resolution of 1 host. at 08:47, 0.08s elapsed
Initiating Connect() Scan at 08:47
**Scanning p508057E1.dip.t-dialin.net (80.128.87.225)** [1697 ports]
**Discovered open port 21/tcp on 80.128.87.225**
Connect() Scan Timing: About 13.94% done; ETC: 08:51 (0:03:06 remaining)
Completed Connect() Scan at 08:49, 130.08s elapsed (1697 total ports)
Host p508057E1.dip.t-dialin.net (80.128.87.225) appears to be up ... good.
Interesting ports on p508057E1.dip.t-dialin.net (80.128.87.225):
Not shown: 1696 filtered ports
PORT   STATE SERVICE
**21/tcp open  ftp**

Nmap finished: 1 IP address (1 host up) scanned in 130.164 seconds
**asmoore@eddy:~$** sudo nmap -v -P0 -p21 -A **80.128.87.225**

Starting Nmap 4.20 ( http://insecure.org ) at 2007-08-28 08:50 EDT
Initiating Parallel DNS resolution of 1 host. at 08:50
Completed Parallel DNS resolution of 1 host. at 08:50, 0.00s elapsed
Initiating SYN Stealth Scan at 08:50
**Scanning p508057e1.dip.t-dialin.net (80.128.87.225)** [1 port]
**Discovered open port 21/tcp on 80.128.87.225**
Completed SYN Stealth Scan at 08:50, 0.27s elapsed (1 total ports)
Initiating Service scan at 08:50
Scanning 1 service on p508057e1.dip.t-dialin.net (80.128.87.225)
Completed Service scan at 08:50, 29.41s elapsed (1 service on 1 host)
Warning:  OS detection for 80.128.87.225 will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port
Initiating OS detection (try #1) against p508057e1.dip.t-dialin.net (80.128.87.225)
Retrying OS detection (try #2) against p508057e1.dip.t-dialin.net (80.128.87.225)
Initiating gen1 OS Detection against 80.128.87.225 at 42.431s
Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port
For OSScan assuming port 21 is open, 32848 is closed, and neither are firewalled
For OSScan assuming port 21 is open, 36135 is closed, and neither are firewalled
For OSScan assuming port 21 is open, 35937 is closed, and neither are firewalled
**Host p508057e1.dip.t-dialin.net (80.128.87.225) appears to be up ... good.**
Interesting ports on p508057e1.dip.t-dialin.net (80.128.87.225):
PORT   STATE SERVICE VERSION
21/tcp open  ftp?
**Device type:** general purpose|router|printer
Running (JUST GUESSING) : **Microsoft Windows NT/2K/XP|2003/.NET** (91%), Juniper JUNOS (85%), Canon embedded (85%)
Aggressive OS guesses: Microsoft Windows XP Pro SP2 (91%), Microsoft Windows 2000 Server SP4 or 2003 Server Standard Edition (91%), Microsoft Windows 2000 SP4 (88%), Juniper Networks router M10i running JUNOS 7.2R1.7 (85%), Canon iR 2200 printer (85%)
No exact OS matches for host (test conditions non-ideal).
TCP Sequence Prediction: Difficulty=0 (Trivial joke)
IPID Sequence Generation: Busy server or unknown class

OS and Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 68.974 seconds
               Raw packets sent: 107 (11.772KB) | Rcvd: 62 (3714B)
```

conclusion: yet another [kiddie]("http://en.wikipedia.org/wiki/Script_kiddie") at work/play \\:D/

if it continues for too long I would add the IP to your /etc/hosts.deny file.

---

### Post by Hopeless on 2007-08-28
neat thing you did there....

thanks for explaning

---

### Post by kornface13 on 2007-08-28
what log did you find that in?  syslog?

---

### Post by Hopeless on 2007-08-29
It's under Debug..

ok he hit me about 1000 times this morning when i was asleep the ip changed a little...I found this code...

```
The below script may work a little better... Note that you'll need a rule in your firewall script to create the TREASON rule set, and jump to it in the beginning, and make a cronjob to run the script so it's automagic.

Something like the following should be in your main firewall script:

---cut---

iptables -F TREASON
iptables -X TREASON
iptables -N TREASON

... (your rest of the rules)

iptables -j TREASON # insert before state established and other lines

---cut---

Then, the below script should be in a cronjob (run once every whatever interval you feel fit).

---cut---
#!/bin/bash

# Stupid shell script to stop stupid TCP Treason attacks
# Setup cronjob to stop them

# First, flush and clean Treason rules
iptables -F TREASON
#iptables -X TREASON
#iptables -N TREASON

for ATTACKER_IP in $(dmesg | grep 'Treason uncloaked!' | cut -d' ' -f5 | cut -d':' -f1 | sort --unique)
do

FOUNDIT=0

for DONTBLOCK in $(route -n | grep -v Destination | grep -v Kernel | awk '{print $2}' | sort | uniq && ifconfig -a | grep inet | cut -f 2 -d ':' | cut -f 1 -d ' ' | sort | uniq)
do
# echo "Checking $DONTBLOCK against $ATTACKER_IP ..."
if [ "$DONTBLOCK" = "$ATTACKER_IP" ]; then
# echo "UHOH! Hacker using forged local IP! Don't block it!"
FOUNDIT=1
fi
done

if [ "$FOUNDIT" = "0" ]; then
# echo "Hacker IP $ATTACKER_IP not found in don't block list... Dropping"
iptables -A TREASON -s $ATTACKER_IP/32 -j DROP
fi
done
iptables -A TREASON -j RETURN

---cut---

```

thanks..

---

### Post by Hopeless on 2007-08-29
found:

[http://www.linuxquestions.org/questions/showthread.php?t=539469](http://www.linuxquestions.org/questions/showthread.php?t=539469)

which said instead of doing iptables upgrade the kernel and will fix it...

so i updated kernel from:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

will wait n see..

thanks

---

### Post by Hopeless on 2007-09-05
nope don't work still getting them...

here is my firewall..
# Generated by iptables-save v1.3.6 on Wed Aug 29 17:37:14 2007
*filter
:INPUT ACCEPT [413:23830]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [433:136061]
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
-A INPUT -j DROP 
COMMIT
# Completed on Wed Aug 29 17:37:14 2007

where does
[COLOR="Red"]iptables -F TREASON
iptables -X TREASON
iptables -N TREASON[/COLOR]
go under????
[COLOR="SeaGreen"]OUTPUT ACCEPT
INPUT ACCEPT[/COLOR]
or seperate?

please help... ;(


thanks

---

