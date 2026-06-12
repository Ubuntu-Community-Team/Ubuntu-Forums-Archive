---
title: "Tor connect problem not using firewall"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by gameguy15 on 2008-03-23
Ubuntu 7.10 ,netopida modem 2241n-itel, iowatelecom ISP

I am running into a weird problem that is happing in both my windows xp system and my Ubuntu when trying to run tor relay.(I have given up on my windows xp i just want my Ubuntu system to work) After following a guild on the net to build tor from source and Vidalia. I am able to run Vidalia have it start tor, and it then finds and open a circuit.(So far so good) I then run into a problem when it checks to see if the ORPort and DirPort are reachable i get the error saying that there are not reachable check firewalls, ports address.... It has no router hooked up to it, just a dsl modem that my ISP says has no firewall. I am running Tor on default ports. 9001,9030 I had the same problem on my xp computer, and it dosn't go away with or without a router hooked up to it with portfowarding. Is this a problem with my modem? I think there has got to be something wrong with my modem or my ISP blocking crap.

---

### Post by bloodniece on 2008-03-25
Some DSL modems have rudimentary firewalls.  Is yours a Westell?

If your modem has an admin config, gain access and set your router's IP as DMZ and then set your Ubuntu computer as DMZ from the router's admin page.  This will rule out any NAT that may be interfering with Tor.

I set Tor up on a cable ISP and Tomato firmware wrt54gl and on a Juniper firewall w/ T3 with no problems.

---

