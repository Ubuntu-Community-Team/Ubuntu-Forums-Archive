---
title: "Internet Connection"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by ricardo.ssouza on 2006-12-04
How can I connect the internet from a terminal?
Can somebody help me?

---

### Post by jordanmthomas on 2006-12-04
what kind of connection are you trying to get up?
ethernet, wireless, a normal modem?
In general
```
ifconfig
```
shows your interfaces
```
sudo ifup ethx
```
brings it up.

If you need to browse the Internet, try lynx or links
```
sudo aptitude install lynx
```

---

### Post by Voxxi on 2006-12-04
What do you mean by that? Do you mean a web-browser on the terminal? Need a little more information before we can help you. ;)

---

### Post by ricardo.ssouza on 2006-12-04
It's a Ethernet connection. I don't want a browser..I just want to connect so I can use the apt

---

### Post by jordanmthomas on 2006-12-04
It is probably eth0 then.
```
sudo ifup eth0
```
...assuming you are using DHCP 
otherwise, you need to configure it using ifconfig, which I am not personally familiar with

---

