---
title: "How to make DNS Settings permanent?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Alex74447 on 2007-06-09
Hey guys. I don't know if this is an easy fix or something, but it seems like it.
On this computer I always have to add 192.168.0.1 to the DNS Servers list on every boot to enable internet browsing. Well this is getting a bit annoying. Is there any configuration file I can edit so that it automatically does that for me? Thanks!

---

### Post by sreenivas1234 on 2007-06-09
yes, i too had the same problem, when i run OS from Live cd after i installed it  and updated it got corrected automatically.

i think when we use live cd the data wont be stored i guiess, better install and try

---

### Post by Alex74447 on 2007-06-09
It's not on the live CD. Weird. Oh well it's not that annoying.

---

### Post by zvacet on 2007-06-10
If you did previous steps right then after adding nameserver in DNS tab 

```
pppoeconf
```

---

### Post by Alex74447 on 2007-06-10
Said access concentrator did not respond.

---

### Post by zvacet on 2007-06-10
system>administration>nrwork>select your modem>properties>select type of connection(dhcp or static)>close>DNS tab>remove nameserver you find there ans put yours instead>close

```
pppoeconf
```

---

