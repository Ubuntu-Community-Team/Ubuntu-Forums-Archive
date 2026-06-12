---
title: "Disabling Ethernet"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by JordanII on 2008-01-06
how should I go about disabling my ethernet? Thanks! :)

---

### Post by Dr Small on 2008-01-06
You could try commenting out your ethernet interface from /etc/network/interface:
```
gksudo gedit /etc/network/interface
```

Dr Small

---

### Post by JordanII on 2008-01-06
> **Dr Small said:**
> You could try commenting out your ethernet interface from /etc/network/interface:
```
gksudo gedit /etc/network/interface
```

Dr Small

The document is blank. :P

---

### Post by JordanII on 2008-01-06
oops! I for got to say that it's a live CD.

---

### Post by p_quarles on 2008-01-06
Temporarily, or permanently?

To shut it off temporarily, run
```
sudo ifdown eth0
```
To turn it back on:
```
sudo ifup eth0
```

---

### Post by JordanII on 2008-01-06
> **p_quarles said:**
> Temporarily, or permanently?

To shut it off temporarily, run
```
sudo ifdown eth0
```
To turn it back on:
```
sudo ifup eth0
```


it doesn't work. :-P

---

### Post by p_quarles on 2008-01-06
What's the output of this command?:
```
ifconfig -a
```

---

### Post by JordanII on 2008-01-06
> **p_quarles said:**
> What's the output of this command?:
```
ifconfig -a
```

eth0 Link encap:Ethernet HWaddr 00:40:CA:91:AB:A7

UP BROADCAST MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000

RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

Interrupt:17 Base address:0x2000


lo Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:1010 errors:0 dropped:0 overruns:0 frame:0

TX packets:1010 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:76652 (74.8 KiB) TX bytes:76652 (74.8 KiB)


ra0 Link encap:Ethernet HWaddr 00:1A:70:AD:11:53

inet6 addr: fe80::21a:70ff:fead:1153/64 Scope:Link

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:25295 errors:74 dropped:0 overruns:0 frame:0

TX packets:21756 errors:0 dropped:0 overruns:0 carrier:0

collisions:113 txqueuelen:1000

RX bytes:2362817 (2.2 MiB) TX bytes:6128 (5.9 KiB)

Interrupt:20

---

### Post by p_quarles on 2008-01-06
Okay, well I have to admit that I've never tried using "sudo" in the live CD desktop environment, so it may have something to do with that. What exactly happens when you run the "ifdown" command? What happens when you run the following?:
```
sudo ifconfig down eth0
```

---

### Post by JordanII on 2008-01-06
> **p_quarles said:**
> Okay, well I have to admit that I've never tried using "sudo" in the live CD desktop environment, so it may have something to do with that. What exactly happens when you run the "ifdown" command? What happens when you run the following?:
```
sudo ifconfig down eth0
```

ifdown command says that eth0 is not configured and ifconfig down says that it's an unknown host.

---

### Post by ugm6hr on 2008-01-06
> **JordanII said:**
> how should I go about disabling my ethernet? Thanks! :)

Why?  From your ifconfig output, it's not transmitting data anyway (looks like your wifi is connected)

---

### Post by JordanII on 2008-01-06
> **ugm6hr said:**
> Why?  From your ifconfig output, it's not transmitting data anyway (looks like your wifi is connected)

The wifi is conected, but I'm not getting internet. :-P

---

### Post by p_quarles on 2008-01-06
Well then, the problem is with your wifi, not with the ethernet NIC. As ugm6hr pointed out, your ethernet card isn't in use.

---

### Post by JordanII on 2008-01-06
> **p_quarles said:**
> Well then, the problem is with your wifi, not with the ethernet NIC. As ugm6hr pointed out, your ethernet card isn't in use.

ok, thanks

---

