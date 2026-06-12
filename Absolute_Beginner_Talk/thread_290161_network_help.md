---
title: "network help"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by threehundred on 2006-10-31
hello. i am not sure if i am doing something wrong but here it goes. it seems i can only connect to certain websites...[www.mozilla.com](www.mozilla.com), ubuntu.com, portableapps.com, but thats seems to be about it. everything else eventually times out....any ideas? also i could not connect to gaim. i am on dsl, lynksys router, hard wired. any help would be much appreciated, thanks!

---

### Post by deepwave on 2006-10-31
Hmm... possibly your system can't figure out the route fast enough.  Try running:

route

If it takes a long time, you may have a routing table issue.  Also maybe your default gateway will not show up.

---

### Post by CatKiller on 2006-10-31
People have reported problems with IPv6 in the past. You could look at turning IPv6 support off - in firefox at first, and then system-wide if you find that you have problems with Synaptic too. It's an about:config option in Firefox, but I can't remember for the system-wide setting.

---

### Post by threehundred on 2006-10-31
i tried running route, it came back fast. the default gateway is set to 192.168.241.1

i am still unable to access a lot of network resources.

---

### Post by threehundred on 2006-10-31
wow the ipv6 worked for the browser, thanks a lot...now i need to figure it out for the whole system. thanks so much!

---

### Post by deepwave on 2006-10-31
Try using Network Tools for system wide network configuration.

---

