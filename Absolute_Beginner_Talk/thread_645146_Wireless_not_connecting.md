---
title: "Wireless not connecting"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by laffinet on 2007-12-19
Hi,

my wireless connection is somewhat erratic. Most of the time it connects just fine, but every now and then it just won't connect.

My setup:
- no Network manager
- wireless configured with [this guide]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+security"), using wpa1 and dhcp

As I said it works fine most of the time, but sometimes I have no connection.
If I then check via
```
iwconfig
```
I can see the wireless network on eth1 (with excellent signal strength, but unassociated) but if I do a 
```
iwlist scan
```
I get "no scan results" for eth1.

If I then try to restart the network with:

```
/etc/init.d/networking restart
```

I get "no dhcp offers received - sleeping"

All I can do then is keep on trying and eventually it will work again. Very annoying.

Any ideas ?

---

### Post by Joeb454 on 2007-12-19
I think it'd be helpful if you have a network manager, it does most of the "behind the scenes" stuff for you :)

---

### Post by RomeReactor on 2007-12-19
Hi. If you don't want Network Manager, maybe you could give [WICD]("http://wicd.sourceforge.net/download.php") a try.

---

### Post by laffinet on 2007-12-19
Well,I had lots of trouble with Network Manager and quite a few threads suggested issues with it so I followed the recommendations, removed it and set up the network manually. As mentioned, it normally works quite well but I have these weird problems every now and then.

---

### Post by laffinet on 2007-12-19
Bump

---

### Post by jimrz on 2007-12-19
> **laffinet said:**
> Well,I had lots of trouble with Network Manager and quite a few threads suggested issues with it so I followed the recommendations, removed it and set up the network manually. As mentioned, it normally works quite well but I have these weird problems every now and then.

I had a brief period using gutsy where I would occasionally have nm drop signal on one of my laptops (strangely the other which uses the same chipset did not do this).  This seems to have been fixed by the recent update to nm. At least, I have not had any drops since it came out.

ps - I found that, when it used to drop, the quickest and surest way to get it working was to bounce the router. It would then be able to connect immediately.

---

### Post by laffinet on 2007-12-19
What do you mean by "bounce the router" ? I guess switch it on and off ? SOmetimes helps, sometimes doesn't. As I said, weird.

---

