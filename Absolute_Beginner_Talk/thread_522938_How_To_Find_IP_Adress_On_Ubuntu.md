---
title: "How To Find IP Adress On Ubuntu"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Pioneer5000 on 2007-08-11
Hey i was wondering how you find your ip address on linux ubuntu cause i remember on windows you just went Run ---> Command > Ip Config . So  was wondering if there was a way well im pretty sure there a way to get this infomation so i can find my ip address. Thank you in advance.

---

### Post by Eastisle on 2007-08-11
This site can give you your ip: [http://www.watismijnip.nl/](http://www.watismijnip.nl/)

---

### Post by wjp.reg on 2007-08-11
> **Pioneer5000 said:**
> Hey i was wondering how you find your ip address on linux ubuntu cause i remember on windows you just went Run ---> Command > Ip Config . So  was wondering if there was a way well im pretty sure there a way to get this infomation so i can find my ip address. Thank you in advance.

Try ```
ifconfig
``` in a terminal window

System | Admin | Net Tools can give you this info too

---

### Post by wjp.reg on 2007-08-11
> **Eastisle said:**
> This site can give you your ip: [http://www.watismijnip.nl/](http://www.watismijnip.nl/)

All that gave me was my internet provider´s IP :-)

---

### Post by xlinuks on 2007-08-11
In Linux you use the "ifconfig" command.
If you just type it and hit enter you get a lot of info including your IP address, but it also supports a lot of arguments. just type "ifconfig --help".

---

### Post by raja on 2007-08-11
```
ifconfig
```
The 'inet address' of the device that is connected to the internet is your ip address.

---

### Post by Pioneer5000 on 2007-08-11
ok, thanks to everyone for replying. :)

---

