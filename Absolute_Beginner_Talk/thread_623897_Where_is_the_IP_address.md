---
title: "Where is the IP address?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mjason on 2007-11-26
I am trying to find the IP address on my laptop. Can anyone help me?

---

### Post by PetePete on 2007-11-26
open a terminal and type
ifconfig

---

### Post by nickpaton on 2007-11-26
Hi and welcome to the forums and ubuntu.

Open a terminal (Applications > Accessories > Terminal) and type in the following:

```
ifconfig
```

This will list your LAN ports and the second line of your active port will start with inet addr: your-IP-Address.

Nick

---

### Post by newlinux on 2007-11-26
type:
```

ifconfig

```

look for inet addr in the output

---

### Post by candtalan on 2007-11-26
> **PetePete said:**
> open a terminal and type
ifconfig

Yes, this will show the laptop IP address as requested. However, if the machine is connected to a router via ethernet cable or wifi then the laptop may have a local address such as, say, 192.168.1.40 while the router will hold the IP address of the 'household' connection and give local addresses to the household laptop/s. If the OP has this situation and wants the household IP address, then probably a browser connection to the router may be necessary.

---

### Post by monte48lowes on 2007-11-26
Click [here]("http://whatismyip.com"). This will tell you the IP address that you are connected to the internet with. 

Mike

---

### Post by seventhc on 2007-11-26
You could go to [http://whatismyip.com/](http://whatismyip.com/) and it will give you your public ip

---

### Post by seventhc on 2007-11-26
> **monte48lowes said:**
> Click [here]("http://whatismyip.com"). This will tell you the IP address that you are connected to the internet with. 

Mike

lol I think we both posted at the same time, well you were obviously faster than me. :lolflag:

---

### Post by nickpaton on 2007-11-26
Hey good one you guys! thanks from here!

Nick

---

