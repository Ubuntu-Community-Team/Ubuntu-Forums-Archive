---
title: "ip address"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by watsgoodg on 2008-02-12
Hey Guys,  

I cant figure out how to find my ip address...i know i can go to whatismyip.com but how can i find my internal.  Thanks. 

-j

---

### Post by taurus on 2008-02-12
You mean

Applications -> Accessories -> Terminal
```
/sbin/ifconfig
```

---

### Post by frodon on 2008-02-12
Type "ifconfig" in a terminal, you should see all your network informations.

---

### Post by ILYA99 on 2008-02-12
Also type in terminal
 
```
 ip addr 
```
 
The output includes ip address.

---

### Post by az on 2008-02-12
System - Administration - Network tool.  Select your Eth0 interface.

(Let's see how many other ways there are...)

You could also look into your router's attached devices page...

---

### Post by watsgoodg on 2008-02-12
Thanks guys for the reply's.  I installed firestarter firewall and i wanted to test.  Thanks again.

---

