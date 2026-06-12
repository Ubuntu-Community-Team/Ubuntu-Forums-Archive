---
title: "not specifying ports"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by ronaldor9 on 2007-11-21
is it possible to acces my ftp without having to specify the port ie [www.domain.dyndns.org:1988](www.domain.dyndns.org:1988)

??
thanks

---

### Post by fastTalker on 2007-11-22
FTP defaults to port 21.  (ftp clients will send requests to port 21 by default.)  so if you set up your ftp server listen on port 21 you will not have to specify the port when you are trying to access the server.  Or if you are using a router to forward port 1988 to the machine running the ftp server, have it forward port 21 to 1988 on your server machine instead.

---

### Post by ronaldor9 on 2007-11-22
would this work if my isp blocks port 21
that is why i used port 1988 beacuse my port 21 is blocked i might call to see if then can unblock it

im trying to think of ideas to tell my isp as to why to ublock it ?? hehe il take suggestions

---

### Post by Dr Small on 2007-11-22
If you have a router, you would open port 1988 and forward it on your router to port 21 on your network IP Address.
If you don't have a router, you'll have to configure FTP to listen on a differnt port.

---

### Post by ronaldor9 on 2007-11-22
yes i have a router but would that still work if i have port 21 blocked from my isp

so step by step this is what i do
ftp port is set to 1980
forward port 1980 on my router
forward port 1980 and host port to 21 ??\
correct i didi this and did not work

---

### Post by ronaldor9 on 2007-11-23
im pretty sure its beacuse telus blocks my port 21  is there any work arounds for this

such as how no-ip allows you to host a website on a diff port but you dont have to specify it when you are typing the name

---

