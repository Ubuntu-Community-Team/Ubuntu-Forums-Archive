---
title: "setting network connection speed at startup"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by zorog on 2007-11-01
Hi everyone,

I've just installed 7.10 on my shiny new computer ;)

however due to a problem with our ADSL router I need to connect to the network at 10mb/s this is fine as out connection to the magical internet pipes is noware near this fast.

at the moment i just run:

> sudo ethtool -s eth0 speed 10 duplex full autoneg off

each time I boot up.... so I would like to** automate this process** I'm sure this is trivial.

**so my question is:** 

how do I set my network card(eth0) to permanently connect at 10mb/s in full duplex mode?

thanks for you time!

have fun,
Simon.

---

### Post by ghpearson on 2007-11-01
edit /etc/rc.local and place you ethtool command there.  You won't need to type the sudo part.
ex;
echo "ethtool -s eth0 speed 10 duplex full autoneg off" >> /etc/rc.local

notice the double >> for adding to the end of the rc.local file.
Hope this helps

---

