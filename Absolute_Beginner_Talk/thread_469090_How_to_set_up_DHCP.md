---
title: "How to set up DHCP"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by dsosb on 2007-06-09
I just installed Feisty Fawn and I am learning Ubuntu for the first time. I have to set up a DHCP server . Does anyone know what packages I need to install to do that or how I go about setting up this kind of server? have one week to learn how to do this. Any help would be appreciated.

Thanks

---

### Post by darkfame on 2007-06-09
There are several DHCP servers available in the repositories. I suggest using dhcp3-server.

How to install:
```
sudo apt-get install dhcp3-server
```

The config dhcpd.conf is located in /etc/dhcp3-server if I remember correctly.

How to list all files installed in that package.
```
dpkg -L dhcp3-server
```

To locate the config files:
```
dpkg -L dhcp3-server | grep /etc
```

---

### Post by dsosb on 2007-06-09
Thank you. Is there a way to do this graphically?

---

