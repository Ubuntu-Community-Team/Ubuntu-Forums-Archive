---
title: "sudo apt-get install through proxy"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-07
As I connect to the internet at school through a proxy server, how can I change sudo-apt get so that it goes through a proxy?

Thanks,
ajeffreys

---

### Post by Clay_Banger on 2007-06-07
type in a terminal:
```
sudo nano /etc/apt/apt.conf
```
then copy this into the newly created file and edit it suit your needs, replacing proxy with the name/ip of your proxy, replacing port with the port etc.

if you need to use a user name and password:
```
Acquire::http::Proxy
"http://username:password@proxy:port";
```
or if you dont need to use a user name:
```
Acquire::http::Proxy
"http://proxy:port";
```

---

