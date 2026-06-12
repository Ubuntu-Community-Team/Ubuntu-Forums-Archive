---
title: "[SOLVED] Does the firewall start automatically while booting ?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-09
I get this while booting:[B]

Starting Firestarter firewall.................[COLOR="Red"]fail![/COLOR][/B]

I know that firestarter is just the GUI but I'm worried about security. 
Thanks.

---

### Post by 3rdalbum on 2008-03-09
You only need a personal firewall if you are running services that would otherwise be open to a local network or to the Internet.

A stock Ubuntu install does not run any such services.

You only need a firewall if you are running something like a testing web server, and are not already behind an ADSL modem-router's built-in firewall.

---

### Post by hyper_ch on 2008-03-09
firestarter is the gui... so no wonder it fails upon booting when there's no xserver running...

---

### Post by vishzilla on 2008-03-09
Run the port scan in Shields up, you will get all ports as Closed! Then you know your firewall is working

---

