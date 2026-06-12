---
title: "AntiVirus/Firewall - needed?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by fzf3 on 2006-09-03
I'm in the process of migrating from XP to Linux and it's going well, so far. 

Under XP, I scrupulously kept my Norton and ZoneAlarm up to date and did all the basic things to avoid problems, like never opening unexpected email attachments, etc.

So, my question is: Do I need AV/Firewall software running under Ubuntu and be equally wary of unexpected email attachments, etc?  I'm using Thunderbird for email.

I notice that AVG has released a free version of its AV software for Linux. Should I install?

---

### Post by Omnios on 2006-09-03
Basicly most say you do not need a anti virus or even a firewall. There is no real virus thread for linux and most run clam antivirus to protect there or other windows machines. There is a firewall run as default and there is firestarter wich is a graphical front end for ip tables.

---

### Post by Dinerty on 2006-09-03
The average user will not need anti-virus installed, like previously mentioned if you run a mail server or want to protect your windows friends then you could install ClamAV, however if your browsing the net for your own personal use I would not bother.

Firestarter is a gui for the built in ubuntu firewall, I personally use firestarter just to have a nose about now and then, but if your connected through a router with a built in firewall you should be ok :)

---

### Post by Omnios on 2006-09-03
> 
connected through a router with a built in firewall you should be ok


 As learnt from G4TeckTV a router firewall is the most secure option. In a software firewall the firewall is already defeated in that the connection has already reached the computer causeing a vulnerability that it can be defeated. In a router firewall the connection has not reached the computer yet therefore would be very hard to deafeat

---

### Post by GeneralCody on 2006-09-03
Well...

If you do have a router with a firewall, make sure that the firmware is updated.
There are numerous exploits in common routers, that makes hacking them a piece of cake. 

I, as a security consultant, would not recomend running Linux without a software firewall.
After all, that is one of the Linux TCP/IP stack's strengths.

If you decide you want firewall protection, go for a iptables based setup.
There are plenty of good GUI (graphical) user frontends for that purpose.

I personally like fwbuilder, witch is in your package sources.  

It is allways good to be on the safe side. 

When it comes to viruses, i would agree that for most personal uses, that would be unnessecary. If you share files with a Windows machine via Samba, it would definetly make sense, but I guess you are not.

Happy hacking!

GeneralCody

---

### Post by fzf3 on 2006-09-03
Thanks.

I'm not behind a router, so I guess I should consider a software firewall, then.

I think the only thing  no-one covered was email attachments. Am I right in thinking that Linux is not vulnerable to the possible viruses/scripts these might contain?

---

### Post by GeneralCody on 2006-09-05
In most cases, no. Email viruses depend on some sort of executable code, that can compromise system security. Linux and Unix is built so that ordinary users do not have access to do things that imposes such risks (mostly).

Besides 99,9% of email viruses target Windows Operating Systems, and therefor can not be executed on Linux.

You should be safe. Keep to the obvious rules:
* Do not log in as root (disabled by default in ubuntu)
* Do not accept actions performed by attachments from sources you do not trust

GC

---

### Post by SkyNet2029 on 2006-09-05
As posted above, the malicious code would need to be executable in order 
to perform an action. Since any foreign code is NOT executable by 
default in Unix/Linux by default, you are safer than your windows 
counterparts. As you have the ability to enable the execution of the 
attachments common sense still goes a long way. Yes, it is true that the 
majority of viruses,etc. are not targeted at Unix/Linux, 
although Rootkits are. 
As for a firewall, iptables is built in to the Linux kernel and enabled 
by default. 
On the issue of being behind a router: Unix/Linux does not run with any 
open ports by default. Mucking about with a front-end to the iptables 
could allow you to inadvertantly enable (open up) some ports. GUI 
useful mostly if you actually need to reassgin, allocate ports. So, 
unless you a running a web/file etc. server, (because for these 
things an open port is a neccesity) you are still covered, unlike 
Windows, which runs with fully open ports (kind of dumb from a security 
standpoint, but great if you are the typical lazy user who just needs an 
instant connectivity, like for file sharing, lan/wan printing and the 
like). This thread reminds me why I only run Linux...sigh.

---

