---
title: "Tor Problems"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by gnama on 2006-12-27
I did everything it says but i get this Your request for [http://www.google.com/](http://www.google.com/) could not be fulfilled, because the connection to [www.google.com](www.google.com) (127.0.0.1) could not be established.

Is it because im on a router?

---

### Post by taurus on 2006-12-27
From a terminal, what's the output of this command?

```
ifconfig
```

---

### Post by gnama on 2006-12-27
Ok, I think I know why, this is what i get when i run tor in shell 
Dec 27 19:16:26.561 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Dec 27 19:16:26.562 [notice] Initialized libevent version 1.1a using method epoll. Good.
Dec 27 19:16:26.563 [warn] /var/lib/tor is not owned by this user (root, 0) but by debian-tor (114). Perhaps you are running Tor as the wrong user?
Dec 27 19:16:26.563 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Dec 27 19:16:26.563 [err] tor_init(): Reading config failed--see warnings above.
How can I change "debian-tor" to root or my user

---

### Post by halitech on 2006-12-27
never mind, didn't realize what Tor was

---

### Post by gnama on 2006-12-27
> **taurus said:**
> From a terminal, what's the output of this command?

```
ifconfig
```

orion@orion-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:F5:6C:1C:FA
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fe6c:1cfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15982 errors:5579 dropped:0 overruns:0 frame:5579
          TX packets:14582 errors:38 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:12249230 (11.6 MiB)  TX bytes:1580131 (1.5 MiB)
          Interrupt:209 Memory:f8980000-f8990000

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:88:45:F0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:152401 (148.8 KiB)  TX bytes:152401 (148.8 KiB)

---

### Post by taurus on 2006-12-27
Maybe something like

```
sudo chown -R debian-tor /var/lib/tor
```

---

### Post by gnama on 2006-12-27
Still says it belongs to "debian-tor", also privoxy works good.

---

### Post by taurus on 2006-12-27
Oops.  I misread that.  I thought it was the other way around.  Do this then.

```
sudo chown -R root /var/lib/tor
```

---

### Post by gnama on 2006-12-27
thanks, i have one question though, can you set tor up with mplayer?

---

