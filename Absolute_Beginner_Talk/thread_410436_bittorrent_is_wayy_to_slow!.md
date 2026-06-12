---
title: "bittorrent is wayy to slow!?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-04-15
hey guys,

I have DSL and i download normally at 60kb/s but with bittorrent i download at 2kb/s - 10. i read up on it a bit and found out you can get better speeds by messing with your router.

dose anyone know what i can do to my router to get faster bittorrent speeds?? thanks

---

### Post by nhandler on 2007-04-15
Bittorrent isn't like a normal download. With bittorrent, the more active the file is, the faster it will download. You want as many seeders as you can. What file are you trying to download?

---

### Post by Seisen on 2007-04-15
Did you happen to port-forward the ports on your router if you don't it will cause it to have slow download speeds.

---

### Post by JayDeePlus on 2007-04-15
try bittornado, it should allow you to download multiple torrents, and should be faster.

[www.bittornado.com](www.bittornado.com)

---

### Post by da1nonlymikeo on 2007-04-15
i already use bittornado, i download manny movies some with houndreds of seeders. they just always download slow :(

 and ill check out port forwarding?

---

### Post by Seisen on 2007-04-15
Here is a good website that might help

[http://www.portforward.com]("http://www.portforward.com")

---

### Post by RomeReactor on 2007-04-15
Hi. You should probably also install a frontend to iptables like **Firestarter**, so you can open the ports on your pc. Look for it in Synaptic.

---

### Post by n3tfury on 2007-04-15
> **da1nonlymikeo said:**
> i already use bittornado, i download manny movies some with houndreds of seeders. they just always download slow :(

 and ill check out port forwarding?

awesome.  let's support illegal downloads.  yay.

---

### Post by da1nonlymikeo on 2007-04-15
[http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm)

 i followed this, and now i have 0kb/s :confused:

---

### Post by n3tfury on 2007-04-15
> **da1nonlymikeo said:**
> [http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm)

 i followed this, and now i have 0kb/s :confused:

that sucks.

---

### Post by josephus on 2007-04-15
use one of the ubuntu torrents if you are trying to figure out if your settings are configured properly.  these always load up quickly.

[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

you shouldn't need to mess with iptables/firestarter since everything is permissive by default.

if your router supports upnp then you don't need to mess with port forwarding, but you'll need a client that is upnp-enabled (ktorrent or utorrent).

edit: it's also possible that your isp is limiting your bittorrent traffic.

---

### Post by nike984 on 2007-04-15
By default, ubuntu is totally locked down, and will not allow incoming connections. 
So you must open some port by your own.
To rectify this, just use this command

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

this is the port that the built in ubuntu bittorrent client uses, so this is the example i give. 
just issue that 1 command and you're good to go.
if you want to revert back to how it was before

```
sudo iptables -A INPUT -p tcp --dport 6881 -j DROP
```

Next step is to set the port forwarding police in your router.
Great tutorial is on 
[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)
so have a look on it.

---

### Post by josephus on 2007-04-15
> By default, ubuntu is totally locked down, and will not allow incoming connections. 

Not sure if that is correct.  If you look at a the iptables of a fresh install of ubuntu

```
sudo iptables -L 
```

The policy is by default is to accept all incoming connections.  Ubuntu is secure because by default there are no services listening to any of these ports.

---

### Post by linux_believer on 2007-04-15
You need to tweak the setting... Some of the links posted are a good start. Many ISP, at least in the US, will throttle your bandwidth.

---

