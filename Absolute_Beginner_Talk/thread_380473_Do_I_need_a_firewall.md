---
title: "Do I need a firewall?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Dan_472 on 2007-03-09
Hello

Do I need a firewall?  I just installed Ubuntu 6.06 from the live cd.  I can already cruise the internet.  Is a firewall already built in?  Is a firewall needed?

Thank You

---

### Post by Patrick K on 2007-03-09
There is a firewall installed. You can add a GUI frontend called Firestarter if you like. I did a bit of reading on the installed firewall, called iptables. It looks as though it filters all incoming traffic but allows totally unfettered outbound traffic. As such, it is totally useless to stop a trojan that might find a way on your system. A few days ago there was a post about a mail server that was compromised by a trojan. i don't recall the exact resolution but IIRC he tracked it down and was able to repair his system without reinstalling. Iptables did nothing to halt the outbound trojan traffic. He just happen to notice that traffic was flowing at an unexpected time.

---

### Post by lamalex on 2007-03-09
if you're worried about security install shorewall. It may be a bit scary but it's very worth learning. a very robust tool for editing what iptables will allow and not allow.

---

### Post by Obor on 2007-03-09
You can install Firestarter (gui for iptables) which will help you control firewall but unless you are running services that allow access from outside you don't really need it as all ports should be closed by default.
These two articles should explain things 
[Ubuntu security 1]("http://www.robdian.co.uk/content/view/28/27/")
[Ubuntu security 2]("http://www.psychocats.net/ubuntu/security")

---

### Post by lamalex on 2007-03-09
if you're worried about security install shorewall. It may be a bit scary but it's very worth learning. a very robust tool for editing what iptables will allow and not allow.

---

