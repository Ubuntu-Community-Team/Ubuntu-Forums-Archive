---
title: "opening ports problem"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2008-04-20
Hi!!!
So.. I installed aMule, configured it, imported server list etc.. But every time it connects to a server i gives me message that i have low id because I am behind a router. Now I am 100% sure that I forwarded ports (tcp and udp) correctly on my adsl router. So i tried to open this ports in my Ubuntu. I used this commands:
sudo iptables -A INPUT -p tcp --dport 50000 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 50001 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 50003 -j ACCEPT
(I set this ports in aMule)
Problem is that I still get lowid warning-I am behind firewall or router!!!??? What am I missing??? :confused:

---

### Post by Rocket2DMn on 2008-04-20
You can try using firestarter, it is a GUI interface to configure iptables, it's very convenient
```
sudo apt-get install firestarter
```
System->Administration->Firestarter

---

### Post by _mOrgoth_ on 2008-04-21
resolved... after all I didn't forwarded ports correctly in router.. stupid mistake..

---

