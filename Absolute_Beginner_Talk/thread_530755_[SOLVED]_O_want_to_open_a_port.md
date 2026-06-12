---
title: "[SOLVED] O want to open a port"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Murtadh on 2007-08-20
Hi

I want to open port for Azuerus and one for transmission, I tried :

```
sudo iptables -A INPUT -p tcp --dport 9090 -j ACCEPT
```

nothing came and nothing happened

I tried 

```
iptables -I INPUT -p tcp --dport 50000 -j ACCEPT
iptables -I INPUT -p udp --dport 50000 -j ACCEPT
```

and it gave this lines:

[COLOR="DarkRed"]iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.[/COLOR]


I thought that if I run the terminal as root everything will work ( Alt+F2 ) but this commends doesn't gave me any response in it too, what should I do?

My PC
Ubuntu 7.04 64 bit
DSL D-Link (DSL-2640T)  modem and router

---

### Post by splintercellguy on 2007-08-20
Alt-F2 does not give you root. The sudo command gives you root privileges for a particular command. To get a root shell, do sudo -s.

---

### Post by Hobo Joe on 2007-08-20
You should open ports on your router.

---

### Post by dpar on 2007-08-20
I used Firestarter, the GUI frontend for iptables, to configure my ports.

---

### Post by Dr Small on 2007-08-20
By the way, you should get firestarter, the GUI of iptables, so you can graphically do it, if it would help. Plus, you need to be root (sudo) in order to have permission above.

Dr Small

---

### Post by Murtadh on 2007-08-20
I installed firestarter,  Azureus now give this message when I do NAT test :

[COLOR="DarkRed"]NAT Error - Connect attempt to (your computer) timed out after 20 seconds. This means your port is probably closed[/COLOR]

but when a ran 
```
iptables -L
```
I saw this in the last lines :
```

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50000 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:50000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9090 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:9090 
```

50000 for Azureus and 9090 for transmission.

---

### Post by Murtadh on 2007-08-20
Now I'm testing both torrent programs,  the result is not good!!
Transmission and Azureus are totally dead whin firestarter is On, no DL od UL!  what should I do now ?

---

### Post by dpar on 2007-08-20
Are you using a router, by chance??

---

### Post by Murtadh on 2007-08-22
I use router, but it doesn't block any ports by default.

Any way I found a very useful site that explained Azureus wiki and helped me:

[http://justanothertechblog.blogspot.com/2007/01/azureus-and-ubuntu.html](http://justanothertechblog.blogspot.com/2007/01/azureus-and-ubuntu.html)

---

