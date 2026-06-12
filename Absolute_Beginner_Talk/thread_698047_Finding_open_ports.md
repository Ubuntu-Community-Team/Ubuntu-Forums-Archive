---
title: "Finding open ports"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-15
How to find open ports and close it?

---

### Post by emarkd on 2008-02-15
Unless you've changed something, all of your ports are already closed.  The default Ubuntu installation has this in effect.  The firewall is iptables.

---

### Post by jordanmthomas on 2008-02-15
An easy way to see what ports are open (since some programs DO open up ports to listen on) is to install nmap and use it on yourself
```
nmap localhost
```

---

### Post by agim on 2008-02-15
Ok, I have a relatively new install, haven't really added anything other than deluge that would connect to the network (I also have thunderbird and firefox), and I ran the code suggested above:
nmap localhost

It is telling me that port 631 is open. Can I close this? Is this a problem?

Edit: Found this solution. I guess it has to do with cupsys.
[http://ubuntuforums.org/showthread.php?t=337868](http://ubuntuforums.org/showthread.php?t=337868)

Edit #2: Why would this be open, I thought all ports were closed by default?

---

### Post by jbalazs on 2008-02-15
[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)

---

### Post by jordanmthomas on 2008-02-15
> **agim said:**
> Ok, I have a relatively new install, haven't really added anything other than deluge that would connect to the network (I also have thunderbird and firefox), and I ran the code suggested above:
nmap localhost

It is telling me that port 631 is open. Can I close this? Is this a problem?

port 631 is used by CUPS.  It's safe to leave it open if you print.

edit
I see you made an edit

---

### Post by 3pinner on 2008-02-15
You might also want to log on to [www.grc.com](www.grc.com) and run the 'Shields Up' program there. They will scan for either common ports, or you can choose  to have all ports scanned. Better have a fast connection for that one!

---

