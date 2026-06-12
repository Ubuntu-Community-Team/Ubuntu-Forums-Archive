---
title: "Wireless connection stops when viewing streaming FlASH video"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by tak1150 on 2007-09-04
I have updated Flash player to the latest (the one that came out 08/21/07) and still the problems exists :(

The problem:
When I view streaming flash video, the wireless connection just stops after ~8 seconds. WICD tray icon still says it's connected, but I can't ping even to my LAN computers.

Background:
I am behind a proxy server that is in between ISP and the router. I can view flash video with no problem on my desktop that is also behind this same proxy server. Both desktop and this laptop use Ubuntu 7.04. Both computers use WICD instead of network manager due to some static LAN IP problems. The wireless connection works fine otherwise (ie if not watching flash video).

Thanks for your help!

---

### Post by sbassett on 2007-09-04
What Wireless protocol are you using (ie A,B, or G)?

---

### Post by tak1150 on 2007-09-04
Thanks for replying.
> What Wireless protocol are you using (ie A,B, or G)?
g

---

### Post by tak1150 on 2007-09-04
Are you suggesting that I change the protocol? I may be able to switch to b.

---

### Post by sbassett on 2007-09-04
No, I wanted to make sure that you were in fact using g all the way around, as other protocols can often choke on streaming video, as their top speed is not quite fast enough to keep up.

---

### Post by tak1150 on 2007-09-04
Oh, to give further clues (important one; should've mentioned first, duh),  I **was able to view FLASH video before I put in the proxy server in the DMZ.**

And I know it's NOT a DNS issue because the desktop computer and the laptop use the same DNS (192.168.0.2, the proxy / DNS / dansguardian server).

Oh and before I put in the proxy server, I was using network-manager on both computers.

---

### Post by tak1150 on 2007-09-04
anybody?

---

### Post by tak1150 on 2007-09-04
OK SOLVED!

It had nothing to do with anything I've said so far!
I have recently disabled ipv6 in the hope to make the connection faster and prevent disconnection during some downloading.

So once again, if you are having similar problems, it could be the disabled ipv6. To fix this,

```
sudo gedit /etc/modprobe.d/blacklist
```

find the line
```
blacklist ipv6
```

and comment it out. You may have to restart your computer (easier) or you can do
```
/etc/init.d/networking restart
```

whew :)

---

