---
title: "DSL with PPoE"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by Umbra on 2005-07-06
Im using Kubuntu on AMD64 distribution.

I dont find the way to congifure my DSL conection (PPoE), i just find an assistant for PPP with Dial up service.

Should i do this via commands? If so, how do i do it?  :confused:

---

### Post by valter on 2005-07-06
[QUOTE=Umbra]Im using Kubuntu on AMD64 distribution.

I dont find the way to congifure my DSL conection (PPoE), i just find an assistant for PPP with Dial up service.

Should i do this via commands? If so, how do i do it?  :confused:[/QUOTE]
 [http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)

---

### Post by PaulWiggers on 2005-07-06
try this

sudo pppoeconf

---

### Post by Umbra on 2005-07-07
[QUOTE=valter][http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)[/QUOTE]


> wget -c [http://frankandjacq.com/ubuntuguide/rp-pppoe-3.5.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.5.tar.gz)
sudo tar zxvf rp-pppoe-3.5.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.5/
sudo gedit /usr/share/applications/RP-PPPoE.desktop

And how do you pretend i must use the command wget if im sitll not connected.  :roll:

> try this

sudo pppoeconf

Thx

---

### Post by Umbra on 2005-07-07
Got it working perfectly. Thx   :)

---

