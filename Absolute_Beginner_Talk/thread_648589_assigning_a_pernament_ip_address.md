---
title: "assigning a pernament ip address"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-12-23
im running  a Linux ubuntu 2.6.20-16-server UTC 2007 i686 accessing through SSH Secure Shell client3.2.9 (Build 283)   or i use putty  from an xp computor,
what  i need help with guys is to change the ip address on the ubuntu server to 192.168.1.64    which is on my local network , please could  you show me  command lines how to do it please  in ssh client 
                             many thanks  dougy

---

### Post by Stemp on 2007-12-23
to set your IP you have to edit you /etc/network/interfaces

eg :
```
iface eth0 inet static
address 192.168.1.64
netmask 255.255.255.0
```

---

### Post by doughardy on 2007-12-23
thankyou so much stemp  all sorted now:popcorn:

---

