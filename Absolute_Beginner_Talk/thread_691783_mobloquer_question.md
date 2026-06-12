---
title: "mobloquer question"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-09
hi,

Installed mobloquer, it appears to be working because it blocks absolutely everything.

Do I need to install a version of moblock or does mobloquer do that automatically?  How can I tell if it is using an updated block list?  can I test it? 

Any advice on how to use the program?

Thanks

---

### Post by randy78 on 2008-02-09
You have to install moblock... a quick search on Google would have revealed that for you ;)

Check it out: 
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

# moblock-control start - inserts iptables rules and starts MoBlock
# moblock-control stop - deletes iptables rules and stops MoBlock
# moblock-control restart - restarts MoBlock
# moblock-control reload - rebuilds the blocklist and reloads MoBlock
# moblock-control update - updates the blocklists and reloads MoBlock
# moblock-control status - gives the iptables settings and the status of the MoBlock daemon
# moblock-control test - simple test to check if MoBlock is working

:popcorn:

---

### Post by jimtb on 2008-02-09
If you have installed mobloquer from moblock-deb.sourceforge.net then moblock and moblock-control are installed with it. Mobloquer is just a front end to moblock. 

The default list blocks even the local network addresses, so that's why you can't connect to the internet when moblock is running. The easiest way to fix is is to use mobloquer. Search for IPs like 192.168.178.x in the Logs and stop blocking them by pressing the appropriate button. After restarting moblock you should be able to connect to the internet again. 
You may also want to whitelist outgoing http and https connections so that you can still view blocked websites the IP addresses of which are blocked.

Hope I helped.

---

### Post by TechDragon on 2008-02-09
thank you both for your answers

---

### Post by randy78 on 2008-02-09
Glad to help ;)

---

