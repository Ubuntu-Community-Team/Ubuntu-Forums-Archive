---
title: "[SOLVED] some websites load, but not others"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by kyalee on 2007-09-20
I'm having trouble loading multiple web pages, including cnn.com and our banking site. I've done a search, saw that other people have had the problem. I tried setting **network.dns.disableIPv6** to **true** and restarting, but that had no effect. I don't have a firewall or a router. 

I also tried pinging cnn.com and when I put in 

```
ping -c 3 www.cnn.com
```

I get

```
PING www.cnn.com (64.236.16.20) 56(84) bytes of data.

--- www.cnn.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```

(I have no idea what that means, but the other threads I read suggested it, so I gave it a try.)

I don't think it's an ISP issue since other sites like this one, LiveJournal, Google, etc. are loading fine. Why would some pages load and others won't?

Help?

---

### Post by irish_flu on 2007-09-20
I can load [www.cnn.com](www.cnn.com) just fine, but I can't ping it either.

For starters, try to load CNN via the IP in your ping (type the IP into your browser's url bar).  If it brings up the CNN font page, you have a DNS issue.  If not, then we can move on.

---

### Post by buzzmandt on 2007-09-20
cnn.com loads ok for me, but doing ping fails
 ping -c 3 [www.cnn.com](www.cnn.com)
PING [www.cnn.com](www.cnn.com) (64.236.24.12) 56(84) bytes of data.

--- [www.cnn.com](www.cnn.com) ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

are you using firefox or other?

---

### Post by philinux on 2007-09-20
If you're running firefox run it from terminal in safe mode and see what happens. Close all firefox windows first then type in.
firefox -safe-mode

If you can now browse all your sites it's prob an extension thats causing the problem.

for more info [http://kb.mozillazine.org/Safe_mode#Starting_Safe_Mode](http://kb.mozillazine.org/Safe_mode#Starting_Safe_Mode)

---

### Post by kyalee on 2007-09-20
Okay, I typed 64.236.16.20 into the URL bar, but it's not loading.

I'm in Firefox.

---

### Post by kyalee on 2007-09-20
I started it up in safe mode. The sites still won't load.

EDIT: And now it's working. I guess maybe it was my ISP. Oh well. Thanks for you help, everyone. :)

---

