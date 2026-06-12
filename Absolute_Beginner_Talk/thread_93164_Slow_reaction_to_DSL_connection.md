---
title: "Slow reaction to DSL connection"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Falklian on 2005-11-21
Just installed Ubuntu on a spare machine I had last night, got it all set up nicely and it all seems to be working except for one thing.  Whenever I try to browse a website or use anything that requires an internet connection, it seems to take at least 15 - 20 seconds before it connects to the server, but once connected, there are no problems, downloads come in just fine at my normal download rate (768k DSL connection) and web pages load up nice and fast. All the other machines in the house are running XP (3 Pro, 1 Home) and have no problems connecting to a server whatsoever, it's just the Ubuntu machine.  Network setup is a Netopia 4 port DSL router (not sure on the model number, at work right now) and a Netgear WGR614v4 wireless router.  The Netopia provides DHCP and the Netgear is set up as a switch with two machines hooked up via CAT5's (one being the Ubuntu machine).  I'm fairly new to Linux, I've been messing around with different distros over the past 5 years and have run Redhat, Mandrake, Slackware, Mepis, and probably several others I can't think of off the top of my head.  This is my first foray into Ubuntu and I like it very much, but it's been about 2 years since I last used Linux, so I am quite rusty.  As far as everything is concerned, do I have a problem with my network or might it be something in Ubuntu that I may need to take a look at?

---

### Post by noigeaR on 2005-11-21
i think your router has a problem with ipv6 support (i have the same problem with my zyxel router by the way).
you can turn off ipv6 support in mozilla firefox by typing **about:config** in the firefox address bar. this should open the options page for firefox. use ipv6 as filter or scroll down to the **network.dns.disableIPv6** option, doubleclick on it so it's set to **true**
if this fixes the slow response time in firefox, then ipv6 support is indeed the problem. there is a way to completely disable ipv6 (not only in firefox), but i don't remember how right now.

---

### Post by Falklian on 2005-11-21
Thank you very much, that worked like a charm :cool: 

If you can remember how to totally disable it, I'd like to know, I'm gonna search for a solution in the meantime.

Thanks again :D

---

### Post by strik9 on 2008-02-21
i dont even use a router, hooked straight up to the ADSL modem and this also worked for me, sped it up greatly.
i would also like to know how to completely disable IPv6 if you can remember? (what exactly does this IPv6 do anyways?)

---

### Post by zerhacke on 2008-02-21
To disable IPv6 you add the following line to the bottom of /etc/modprobe.d/blacklist

blacklist ipv6

you will need to be root to do this.

---

### Post by strik9 on 2008-02-23
> **zerhacke said:**
> To disable IPv6 you add the following line to the bottom of /etc/modprobe.d/blacklist

blacklist ipv6

you will need to be root to do this.

sounds great but how exactly does one go about editing this file (or any file in the /etc for that matter)?

---

### Post by shad0w_walker on 2008-02-23
Press Alt-F2 to open the run dialog and run this command:

```
gksu gedit /etc/modprobe.d/blacklist
```

That will open up a prompt for your password (To confirm you are allowed to run admin tasks) and then when you have entered your password just edit it like you would a normal file. Make sure you remember to save before you close it up.

When it's all done the easiest way to apply the change is a quick reboot.

---

