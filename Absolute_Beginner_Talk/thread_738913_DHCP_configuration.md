---
title: "DHCP configuration"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by vasiauvi on 2008-03-29
Hi all,
I have a problem.How can I configure the network for use the internet on Ubuntu?To connect to the internet I have to put a User Name and a Password.I have tried to modify the settings but I didn't managed to connect to internet because I don't know where to put the user and pass.
Thank you very much!

P.S. sorry if are threads with the same subject.I have read some of them, I have tried but i didn't managed to resolve the problem.

---

### Post by SpaceTeddy on 2008-03-29
how are you connected to the internet (physicially) ? are you directly plugged into a modem ?

---

### Post by superprash2003 on 2008-03-29
are you using dsl? or cable technology?

---

### Post by vasiauvi on 2008-03-29
I am pluget with a cable directly to the PC.
But I have managed to configure the dhcp with this "setup":
```

sudo pppoeconf

```
 and in the options that apeares after this comand I have used the user name and password.
This is the link, sorry because is not in english but it has pictures (and I don't know english very well :():
[http://wiki.ubuntu.ro/ConexiuneInternetFolosindProtocolPPOE?highlight=%28ConexiuneInternetFolosindProtocolPPOE%29]("http://wiki.ubuntu.ro/ConexiuneInternetFolosindProtocolPPOE?highlight=%28ConexiuneInternetFolosindProtocolPPOE%29")

---

