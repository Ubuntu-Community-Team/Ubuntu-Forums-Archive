---
title: "Getting my wireless working automatically"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by N Clement on 2007-04-15
Let me just preface this by saying that my wireless does work, and I am truly ecstatic about that since I have the infamous ipw3945ABG card.

I do have to run a few commands to get it going each time though:
```
sudo iwconfig eth1 "[MYNETNAME]"
sudo dhclient eth1
```

If anyone can tell me how to get these as default start up settings, I would be very grateful.

---

### Post by slickidiotfan on 2007-04-15
Give me some background, are you running Network Manager?

---

### Post by N Clement on 2007-04-15
I just have Network Monitor. 

Is editing /etc/network/interfaces the answer?

Right now the section on eth1 is:

```
iface eth1 inet dhcp
wireless-essid [myessid]
wireless-key [mykey]

```

to include```
auto eth1
```
right before that what I need to do?

(of course [myessid] and [mykey] are replacements for the real values because thats a tad bit more than I want to share)

---

### Post by slickidiotfan on 2007-04-15
Oh I use Network Manager, no need for the terminal app with Network Manager.

---

### Post by N Clement on 2007-04-15
Does anyone know if modifying /etc/network/interfaces will work for me?

---

### Post by N Clement on 2007-04-15
I tried doing the afore mentioned edit of the interfaces file, but that did not seem to work.  Any other ideas?

---

