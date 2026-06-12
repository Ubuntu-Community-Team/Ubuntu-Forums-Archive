---
title: "Can't get an ipv4 address, only ipv6???"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by dav7612r on 2007-10-12
Problem is i can't connect to the internet with an ipv6 address. /etc/networking/??? (forgot name of file) is set to give me a dhcp ipv4 address but when i check in networking tools only an ipv6 address is listed for eth0.

how do i fix/force it to give me the ipv4 address?

---

### Post by Dr Small on 2007-10-12
Have you tried restarting the network ?
```
sudo /etc/init.d/networking restart
```

---

### Post by dav7612r on 2007-10-12
I'll try that when i get home tonight. Thank You.

In case that doesn't work does anyone else have any suggestions?

---

