---
title: "was my laptop hacked?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-11-23
Hey!
Yesterday I made a post regarding some strange network activities, here:
[http://ubuntuforums.org/showthread.php?t=620664](http://ubuntuforums.org/showthread.php?t=620664)

We found out, that some server from Japan is doing something with my laptop...
Don't know what.
I already asked the question there, too, should I change all of my passwords? Was my laptop compromised? If yes, then how?? I thought ubuntu is still going strong in security issues...
If non of that above, than what happened?
This was going on for a few days, and the traffic in 1-2 hours was about 300-400 Mb, even if I didn't use any programs that access the network... not that I know of...


So what next, is my question...
Sorry to make another post, but I really need to know...
Thanx

---

### Post by LaRoza on 2007-11-23
When in doubt, assume it was.

---

### Post by hyper_ch on 2007-11-23
and when it was the only option is to resetup the computer...

---

### Post by mhossom on 2007-11-23
Have you tried using Wireshark to capture some of the traffic?  If not, I would.  As long as it is not encrypted, you should be able to see what is going on (ports, protocols...).

---

### Post by seshomaru samma on 2007-11-23
use IP tables to block the address
also you can complain to the ISP at [email]abuse@itscom.jp[/email]

---

### Post by PmDematagoda on 2007-11-23
Try and see if your PC is affected by rootkits.

First install chkrootkit

```
sudo apt-get install chkrootkit
```

then execute

```
sudo chkrootkit
```

to check your PC for rootkits.

If that is clean you could also try rkhunter.

Install rkhunter

```
sudo apt-get install rkhunter
```

then execute

```
sudo rkhunter -c
```

---

### Post by duruttye on 2007-11-23
I installed numerous kits like those you mentioned, but I'm nearly not an expert, so I can't do anything with the results...

In rootkit mostly the output is: nothing found, except for these:

Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/lib/modules/2.6.22-14-generic/volatile/.mounted

Searching for LPD Worm files and dirs... nothing found

next:
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
Searching for LOC rootkit... nothing found

next:
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/usr/sbin/ntop[5325], /sbin/dhclient3[7362])
Checking `w55808'... not infected


And that's it.
Anything makes sence? :D

---

### Post by duruttye on 2007-11-23
Damn!

rkhunter output:

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

So, what now?

---

### Post by hyper_ch on 2007-11-23
and what's that warning about? why is it triggered?

---

### Post by duruttye on 2007-11-23
In the /var/log/rkhunter.log file, it said that found a suspicious file in /dev/shm directory, already deleted it.
Also it found some hidden directories in the /dev:
[14:28:07] Warning: Hidden directory found: /dev/.static
[14:28:07] Warning: Hidden directory found: /dev/.udev
[14:28:07] Warning: Hidden directory found: /dev/.initramfs

Is this normal, or should I delete those too?

---

### Post by hyper_ch on 2007-11-23
[http://ubuntuforums.org/showthread.php?t=600938](http://ubuntuforums.org/showthread.php?t=600938)

---

### Post by duruttye on 2007-11-23
> **mhossom said:**
> Have you tried using Wireshark to capture some of the traffic?  If not, I would.  As long as it is not encrypted, you should be able to see what is going on (ports, protocols...).

Well, yesterday I somehow managed to block the traffic, 'cause today there is none, so I there is no purpose to use these applications, but if it comes back to hunt me, I will keep them in mind.
Thanx

---

### Post by duruttye on 2007-11-23
> **hyper_ch said:**
> [http://ubuntuforums.org/showthread.php?t=600938](http://ubuntuforums.org/showthread.php?t=600938)


Okey, so I'm stuck again.

---

