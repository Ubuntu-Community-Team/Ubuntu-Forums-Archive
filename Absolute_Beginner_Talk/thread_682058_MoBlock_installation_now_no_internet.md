---
title: "MoBlock installation now no internet"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by reesy on 2008-01-29
I have just installed Moblock by following the guide on [https://help.ubuntu.com/community/MoBlock]("https://help.ubuntu.com/community/MoBlock") and once I had finished it my internet connection wasn't working. I then rebooted the computer hoping it would come back and nothing. It's clear that the router isn't the problem as I am using the internet through the same router now. If any one could give some suggestions on how to solve my problem I would be grateful. Thanks.

---

### Post by ridetheteapot on 2008-01-29
You probably need to whitelist your router

find the moblock.conf file in /etc/moblock
and edit the WHITE_IP_IN (and i guess WHITE_IP_OUT) by adding your routers IP (or whitelist the whole subnet ie. 192.168.1.0/24 for the rest of the network)

---

### Post by reesy on 2008-01-30
Thanks for that I know what to do now but when I edti it and save it it says I don't have the permissions, how do I open it so I have permissions?

---

### Post by jan quark on 2008-01-30
```
sudo gedit etc/moblock/moblock.conf
```

the sudo is important and change the directory path to the correct one if that is false I am guessing at that

---

### Post by reesy on 2008-01-30
I have solved the problem now I found the answear in another forum [http://ubuntuforums.org/showthread.php?t=668360]("http://ubuntuforums.org/showthread.php?t=192559")
I had to edit /etc/moblock/moblock.conf, and change the line :
> WHITE_TCP_OUT=""
to
> WHITE_TCP_OUT="80 443"
Thanks any way guys.

---

