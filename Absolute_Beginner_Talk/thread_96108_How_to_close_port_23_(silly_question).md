---
title: "How to close port 23? (silly question?)"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by robenroute on 2005-11-28
Perhaps indeed a silly question, but I did a few web-based computer scans and all of them said my TTS port (23 - Tiny Telnet Server) was wide open! Oops, I guess. Now, how do I go about closing this port? I've already search on the Net and these forums, but didn't find anything directly applicable.

Any help c.q. pointing in the right direction is much appreciated. Thanks.

Rob

P.S. sorry, forgot: using BB and I'm connected via an ADSL modem/router through Ethernet.

---

### Post by danko on 2005-11-28
Install firewall. Look for Firestarter or Guarddog.

---

### Post by casper_2095 on 2005-11-28
Uninstall the "telnetd" package, 

or whatever service it is you are running on that port.

*edit*
oh. you said "web-based scan".  It might be your modem which has a "telnet" feature which is open to the internet.  Check the manual for the modem and turn that off, or change it to only respond to the internal network.

---

### Post by robenroute on 2005-11-28
casper_2095,

You might be right with your comment concerning the modem/router. I'm not running any telnet daemon, nor any other program using port 23 (as far as I can tell). So, I guess I can stop worrying....

Thanks a lot for your response, both of you.

---

### Post by ranf on 2005-11-28
[QUOTE=robenroute]
You might be right with your comment concerning the modem/router. I'm not running any telnet daemon, nor any other program using port 23 (as far as I can tell).[/QUOTE]
Find out (list programs that listen to IP ports):
```
 sudo netstat -lptnu
```

---

