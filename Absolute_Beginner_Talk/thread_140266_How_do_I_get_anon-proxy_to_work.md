---
title: "How do I get anon-proxy to work?"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Frigo on 2006-03-05
Hi everybody!
I'm really new to Ubuntu....
I have downloaded with the Sinaptic Packet Manager "anon-proxy" and I can't get it to work. When I try to start it from the terminal the message "Failed to load main-class Manifest from JAP.jar" appears...
Where am I doing wrong?

thank you in advance....

---

### Post by Bazon on 2006-05-09
+1

I also tried the .jar from the site, but that keeps freezing my system after a while....

the best thing I managed so far is:
```
$ anon-proxy -j -a -d -p 4001
Unable to write pidfile.
```

So has anybody managed to run it?

---

### Post by Bazon on 2006-05-15
update:
Bit more success with
*anon-proxy -j -p 4002 -n mix.inf.tu-dresden.de:6544 -a*
:
```
$ anon-proxy -j -p 4002 -n mix.inf.tu-dresden.de:6544 -a
[2006/05/15-08:33:53, info    ] Anon proxy started!
[2006/05/15-08:33:53, info    ] Mix-Version: 00.02.39
Using: OpenSSL 0.9.8a 11 Oct 2005
Using Xerces-C: 2.7.0
[2006/05/15-08:33:53, info    ] Starting MIX...
[2006/05/15-08:33:53, info    ] Try connecting to next Mix...
[2006/05/15-08:33:53, info    ]  connected!
[2006/05/15-08:33:54, critical] Mux-Channel Receiving Data Error - Exiting!
```
But the Daemon is running untill I quit with CTRL + C
However, no proxy connection working. :(

---

### Post by all4tux on 2007-10-16
i am having the same problem to the T

---

