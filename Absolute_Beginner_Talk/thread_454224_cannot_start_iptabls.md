---
title: "cannot start iptabls"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by che4 on 2007-05-25
I ernter commands as a root user in ternial
service iptables start
it shows as follow
/ust/bin/service:  5: /etc/init.d/iptables: not found
 
but I have been installed all relative packages
Where to check this error

---

### Post by Shazaam on 2007-05-25
[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+howto](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+howto)

Try this for iptables commands ( type it in a terminal window) ...

iptables --help

Go to a site like this one to see what ports are open/closed/stealth..

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If you want a GUI for iptables open Synaptic and search for FireStarter or GuardDog (GuardDog is part of KDE).
Iptables is loaded automatically on boot so you shouldn't have to start it as a service. If you are a Windows user and expect an icon to show up in your panel there are ways to do this but IMHO it's not needed.

---

