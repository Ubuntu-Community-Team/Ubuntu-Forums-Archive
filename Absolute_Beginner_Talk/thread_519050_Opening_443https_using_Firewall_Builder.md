---
title: "Opening 443/https using Firewall Builder"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mareltrout on 2007-08-06
Hello, I'm trying to open up https/port 443 in my firewall on Ubuntu Fawn using Firewall Builder. Firewall Builder seems to make it ridiculously easy to set up this rule. Or so one would think...

HOWEVER, after I set up the rule and compiled and ran the fwbuilder script, I ran nmap against port 443. It tells me that 443/https is closed. Similarly, if I use telnet 127.0.0.1 443 it appears to be blocked.

If I look at the iptables I see the following:

**ACCEPT tcp -- anywhere - [my machine's address] tcp dpt:https state**

Which doesn't look like the examples of enabling ssh in iptables on Debian that I've seen. But hey, what do I know.

Meanwhile, the Firewall Builder gui interface seems to indicate that everything is just ducky. It threw no errors when I compiled and ran the script. Personally, I'd be happy to bypass Firewall Builder and edit iptables directly, but at this stage in my Linux knowledge, I wouldn't want to do that without the guidance of an Eagle Scout.

Also, just so you know, I haven't configured Apache2 yet nor enabled mod_ssh or any of those Web server configs yet. I wanted to make sure the firewall rule was working first.

This is a test server, so I suppose if I botch up iptables it's not the end of the world. I wouldn't mind avoiding that though.

Any suggestions at all...

---

### Post by mareltrout on 2007-08-07
Hey, I figured this one out. Turns out that I had https configured correctly all along. Thanks anyway, guys.

---

