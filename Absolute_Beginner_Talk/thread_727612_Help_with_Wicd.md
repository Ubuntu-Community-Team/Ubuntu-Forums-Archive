---
title: "Help with Wicd"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by True_Nosferatu on 2008-03-17
i just installed ubuntu and i cant connect to my wireless router(linksys) through Wicd. i have a broadcom card and a linksys router and cant see the network in the preferences of Wicd.:confused: help

---

### Post by handydan918 on 2008-03-18
> **True_Nosferatu said:**
> i just installed ubuntu and i cant connect to my wireless router(linksys) through Wicd. i have a broadcom card and a linksys router and cant see the network in the preferences of Wicd.:confused: help

Post the output of ```
lspci | grep -i net
```

and let's see which ($&^$ broadcom card you have. They are a PITA....

---

### Post by True_Nosferatu on 2008-03-18
well it turns out i was wrong and it apparently isnt a broadcom but some integrated card all that i can help with is that it is a gateway Model: mx6453

---

### Post by Papa-san on 2008-03-18
Did you get it working?

If not, post the output of the above command. It will show the necessary information no matter what card you are using.

I'd also suggest (separately):
```
iwconfig
ifconfig
iwlist scan
```

---

