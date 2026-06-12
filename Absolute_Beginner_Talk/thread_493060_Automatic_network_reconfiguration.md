---
title: "Automatic network reconfiguration"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Jimcanoa on 2007-07-05
Hello, I'm having problems with my network, I've changed the network card but I don't know how to tell the system to redetect the network hardware, is there a way to do so? I'm thinking sth like dpkg-reconfigure or sth like that. After changing the network card I don't see the eth0 interface in ifconfig, only 'lo'

thanks in advance!

---

### Post by John.Michael.Kane on 2007-08-03
You can try this from a terminal.

Frist: Should add your card to the list.
```
sudo dhclient
```

Second:Should configured the new card with a new IP
```
sudo dhcpcd
```

---

