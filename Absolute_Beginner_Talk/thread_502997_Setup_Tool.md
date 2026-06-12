---
title: "Setup Tool ?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by wotuzu17 on 2007-07-17
Hi, I already have experience with Linux, but I'm new to the Debian / Ubuntu world:

Questions:
- Is there a setup tool like Suse's YAST?
- How can I access the semi-graphic install program out of the command line

Thanks

---

### Post by jvc26 on 2007-07-17
Semi graphic install program? - Is that synpatic package manager? If so can't you just go to System->Administration->Synaptic Package manager? Or from CLI:
```

gksudo synaptic

```
Il

---

### Post by rickycodie on 2007-07-17
try wubu its a install assister

---

### Post by wotuzu17 on 2007-07-17
thanks for your suggestions. 

I'm using the server version of Ubuntu 7.04, and only have the command line, no desktop.

# gksudo synaptic
# sudo wubu

neither of the commands works

I remember some menu that offers different tasks like 'execute a shell' or 'partitioning' ,..... how to access this menu?

---

### Post by jvc26 on 2007-07-17
```
sudo aptitude
```
Thats the ncurses based version of synaptic, apologies, misunderstood the situation,
Il

---

