---
title: "Which firewall and Anti-virus"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by jd3010 on 2007-10-27
Just installed Ubuntu 7.10 (newbee switched from XP)  and would feel better if I had a Anti virus and a firewall (even though it seems that it would not really be nessary.

Can anybody suggest me a Antivirus (if possible with automatic update and Real scan)

and a firewall. 

Thanks

---

### Post by insane_alien on 2007-10-27
AVG and avast have linux versions IIRC though they will never detect anything that could possibly harm your system(they might detect a windows virus sitting in the cache but it won't do anything.)

as for a firewall, you already have one built into the kernel called iptables. firestarter is a good frontend for it.

---

### Post by nixclusive on 2007-10-27
well you won't really need an antivirus as there not many viruses for linux out there and even if you were infected it won't do much harm due to the way linux works. You already have a mature firewall system in you ubuntu kernel, you might want to install a frontend for it. Try firestarter.. open the terminal and enter: ```
sudo apt-get install firestarter
```

---

### Post by kebes on 2007-10-27
Anti-virus isn't really needed on Linux. You can install "ClamAV" as an anti-virus, but that's really to catch Windows viruses and prevent them from spreading to Windows machines (for example if you're running a file server that Windows computers will connect to).

As for a firewall, Linux is quite secure by default, and has built-in firewall controls (called iptables). You can install "Firestarter", which gives you a convenient GUI for managing that firewall. (And by default creates a more secure "default deny" policy in iptables).

Hope that helps.


P.S.: Both of the packages I mentioned can be installed from the "Add/Remove" menu option or the Synaptic package manager.

---

### Post by funrider on 2007-10-27
FYI, i dun use any of these and never run into any trouble.

---

### Post by jd3010 on 2007-10-27
Thnaks all for the quick reply. Im installinf firestarter right now....

For the AV  is AVG the only one, i read someting about F-Prot ?? 

shall I stay with AVG ??

thanks

---

### Post by jd3010 on 2007-10-27
Again thanks ...

firestarter installed. Any suggetions for the settings or should I leave the default ones ?

---

### Post by Chayak on 2007-10-27
Anti-virus not so much but you need a firewall if you're connected to the internet and not using a router based firewall.  I know some people say linux doesn't need it but it does.  It may not be as easy to crack as windows but it can still be done and a firewall just makes it that much more difficult.  If you don't need remote access then turn off sshd or at least use your router to block requests from the net.  SSH bruteforce attacks are probably the most common attack I see on the unix systems I own and the ones I run at work.  We switched the sshd service to a non-standard port and we're using ssh keys to login.

---

### Post by Chayak on 2007-10-27
> **jd3010 said:**
> Again thanks ...

firestarter installed. Any suggetions for the settings or should I leave the default ones ?

Deny all by default and just open the ports you need.

---

### Post by jd3010 on 2007-10-27
Thanks,

I looked through the Firestartet and did not find anything like sshd ??

DoI have to add rules ? inbound outbound ?? or is it ok with the install *i made just now

Do I enable ICMPand ToS  filtering ?

Enable Block traffic efrom reserved addresses ... ?

Thanks

---

### Post by commonlyUNIQU3 on 2007-10-27
the sshd default port is 22.  I don't have firestarter installed anymore, but there is a fairly straight-forward way of blocking traffic on specific ports that I'm sure you'll be able to figure out...

---

### Post by scorp123 on 2007-10-27
> **jd3010 said:**
>  For the AV  is AVG the only one, i read someting about F-Prot ?? shall I stay with AVG ??  You don't need an anti-virus program ..... I use Linux since 1996 .... to make it short: really, you don't need any AV programs here. Just forget about viruses. They're just a bad memory. Nothing more. :cool:

---

### Post by jd3010 on 2007-10-27
Thanks, so I will just block port 22.

---

### Post by jd3010 on 2007-10-27
> **scorp123 said:**
> You don't need an anti-virus program ..... I use Linux since 1996 .... to make it short: really, you don't need any AV programs here. Just forget about viruses. They're just a bad memory. Nothing more. :cool:
Yeyyyy, must be my Windows background ... but I think I will still try to find one. Is AVG ok ?

---

### Post by scorp123 on 2007-10-27
> **jd3010 said:**
> Yeyyyy, must be my Windows background ... but I think I will still try to find one. Is AVG ok ? No idea. The last time I installed an AV product was August 1996. :lolflag:

---

### Post by michaelzap on 2007-10-27
> **jd3010 said:**
> Yeyyyy, must be my Windows background ... but I think I will still try to find one. Is AVG ok ?

I've used ClamAV and AVG. Both of them are fine for scanning downloads or whatever you want to be sure is free of viruses before letting Windows users access it. I prefer AVG nowadays because ClamAV seems to take a long time to scan and chokes on very large files.

F-Prot is also available, and if you search these forums you'll find tutorials for both it and AVG (ClamAV is in the standard repositories).

---

### Post by jd3010 on 2007-10-28
> **michaelzap said:**
> I've used ClamAV and AVG. Both of them are fine for scanning downloads or whatever you want to be sure is free of viruses before letting Windows users access it. I prefer AVG nowadays because ClamAV seems to take a long time to scan and chokes on very large files.

F-Prot is also available, and if you search these forums you'll find tutorials for both it and AVG (ClamAV is in the standard repositories).
thanks I will try AVG.

---

### Post by jd3010 on 2007-10-28
> **scorp123 said:**
> No idea. The last time I installed an AV product was August 1996. :lolflag:
woahh, seems impossible in the world....

---

