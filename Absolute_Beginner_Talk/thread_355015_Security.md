---
title: "Security?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by rachon on 2007-02-06
Hi to All:
I'm a beginner, Can someone help with do I need to use a fire wall, virus protection, spyware or adware protection? Are any of these needed on a linux system? I dual boot with the much hated windows. I also homeschool and we live on the internet. Once I'm able to configure my printer ( lexmark x7350) I plan to run Ubuntu exclusively.
Than you,
Rachon
[EMAIL="weluvdeere@yahoo.com"]weluvdeere@yahoo.com[/EMAIL]

---

### Post by r4ik on 2007-02-06
Forget about it not needed :)
Welcome to Ubuntu/Linux !

---

### Post by jd65pl on 2007-02-06
Not really much need to worry about virus', spyware etc. for firewall configuration see firestarter, a firewall is included with this distro as standard (iptables)

---

### Post by rachon on 2007-02-07
Thanks so much for all your help. I appreciate it!
Rachon

---

### Post by Sleestack on 2007-02-07
OK, so maybe I'm twice shy having used Windows for so long...is the general consensus here that I do not now, nor ever will require any anti-virus, firewall, etc.?

---

### Post by kpatz on 2007-02-07
The only reason to use an anti-virus on Linux is if you share files with Windows users, or do email from within Linux.  Windows malware can't hurt Linux, but scanning your attachments will help keep you from accidentally forwarding them onto your Windows-using friends.

A base install of Ubuntu doesn't need a firewall either since no services are listening on any ports.  But once you install Apache, OpenSSL, FTP, a mail server, yadda yadda you may want to use firestarter (iptables) to set up some firewall functionality.

---

### Post by Tomosaur on 2007-02-07
> **Sleestack said:**
> OK, so maybe I'm twice shy having used Windows for so long...is the general consensus here that I do not now, nor ever will require any anti-virus, firewall, etc.?

It can never be guaranteed that viruses will **not** increase as time goes on, but at the moment, there's much need to worry. The majority of anti-virus techniques are reactive anyway: there's no way safeguarding against viruses until one appears, and you find out how it got there, what it does, and how to get rid of it. There's no point speculating about it. If viruses begin to appear more frequently, then yes, you may need an anti-virus program, but at the moment, most people aren't too concerned. Linux is very secure anyway - and any exploits which are found are usually fixed within a few days, sometimes even a few hours, of them being reported. As long as you keep everything up to date, you should have no worries.

---

### Post by SunnyRabbiera on 2007-02-07
well actually linux does have viruses but they are rare birds, there are some antivirus programs out there for linux but thier main intention is for windows viruses that might slip in if you use windows programs.
a good antivirus I use for linux is aegis, you can find it in synaptic :D

---

### Post by mcduck on 2007-02-07
Well, nobody can promise that there won't EVER be Linux viruses, but for now you are safe.. Same goes for spyware and such. But currently the only use for antivirus apps in Linux is to scan for Windows viruses, useful if you have a mail server or something but not necessarily in home use. Even less so when all windows machines still need antivirus app..

Firewall? As long as you don't install any server apps that would respond to inbound connections from the net you are safe even without a firewall. But since the firewall is built-in feature of Linux and using it comes with no extra cost on resources you may just as well use it if you like.

---

### Post by Sleestack on 2007-02-07
Thanks, very reassuring. My heart grows fonder for Ubuntu daily.

---

### Post by g3k0 on 2007-02-07
Good luck to anyone attempting to write a virus for linux .. theres so many distros out there.  Theres no need to worry for a long long time.  Linux not being unified does have a benefit after all.  (Though the pros of unification far outweigh the cons)...and wont happen

---

### Post by SunnyRabbiera on 2007-02-07
well actually creating a simplistic binary virus would be pretty easy to do if you are a programmer as the linux source is wide open, its not the distro its the kernel
and at heart practically all linux distros have the same kernel, though some might have more updated kernels then others.

---

### Post by Shatrat on 2007-02-07
Just because something is open source doesnt mean its easy to write a virus for.
I know how padlocks work but I cant open one without a torch or a key.

For the same reasons just because you can write a virus doesnt mean it will do anything unless you can get it executed, preferably with root permissions, on somebody elses machine.  That is a whole lot harder in linux, just like getting a lexmark working is. (lexmark is trash, get an HP).

> **SunnyRabbiera said:**
> well actually creating a simplistic binary virus would be pretty easy to do if you are a programmer as the linux source is wide open, its not the distro its the kernel
and at heart practically all linux distros have the same kernel, though some might have more updated kernels then others.

---

### Post by wildseven on 2007-02-07
Linux is the underdog and has been made through everyone in the community. We all strive in pain building linux up from the ground to where it is now ( god bless you Linus torvald ) lol.
I doubt people will attack the very own system they help create, so virii are rarely seen for linux.

---

### Post by aysiu on 2007-02-07
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

