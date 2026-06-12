---
title: "Wireless problem"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by radink on 2007-11-21
I've just installed ubuntu on my dell laptop. It has an intel 3945 card in it. Wireless is on and It looks like it connects, but I can't surf. I tried setting the wpa to what I have on the router with the same pass, and no go. Any ideas? Using Ubuntu 7.10

---

### Post by oneadvent on 2007-11-21
did you put in the correct dns server?

If not, try out opendns.

can you ping an ip address or the router?

---

### Post by radink on 2007-11-21
DNS servers should be good.. same one as on the desktop pc. Can not ping the router however. Stumped.

---

### Post by oneadvent on 2007-11-21
ping 127.0.0.1

further than that, have you tried a card?

---

### Post by radink on 2007-11-21
I found out the problem. Apparently ubuntu doesn't like it when you have the SSID broadcast off even though I hard code the network name in there. I hope this get's fixed.

---

### Post by spiderbatdad on 2007-11-21
[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

---

### Post by oneadvent on 2007-11-21
I actually haven't had mine off. 

I'm not sure what happens that way. Why not just encrypt it?

Of course, it is still easy enough to hack.

---

