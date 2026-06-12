---
title: "iptables not working this script"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by dapim on 2007-12-17
#open 80 for http
sudo iptables -A INPUT -p tcp -i wlan0 --dport 80 -j ACCEPT

#open 53 for dns
sudo iptables -A INPUT -p udp -i wlan0 --dport 53 -j ACCEPT

#block all
sudoiptables -A INPUT -j DROP

---

### Post by blueridgedog on 2007-12-22
Define "not working".

Also, post the output of:

```
sudo iptables --list
```

and

```
sudo ifconfig
```

---

