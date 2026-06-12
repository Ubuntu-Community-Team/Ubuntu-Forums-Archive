---
title: "Cant connect to internet."
date: 2010-06-12
forum: Apple Hardware Users
---

### Post by applepod124 on 2010-06-12
Hey, I am trying to dual boot OS X and Ubuntu 10.04. Install went well, but I can't seem to figure out how to connect to the internet. when I boot into Mac OS X I can connect, but not in ubuntu. Any help please?
Thanks!

---

### Post by linuxopjemac on 2010-06-12
more info pls, model of your Mac, wireless or wired....questions...

---

### Post by applepod124 on 2010-06-12
> **linuxopjemac said:**
> more info pls, model of your Mac, wireless or wired....questions...
I'm using an iMac8,1. wireless connection.

---

### Post by linuxopjemac on 2010-06-12
Hook it up with a cable, so you are connected then:
```

sudo apt-get update
sudo apt-get upgrade
```

Then you go to System -> Administration -> Hardware drivers

Hopefully you can select the Broadcom driver there.

---

### Post by applepod124 on 2010-06-12
Ok. I'll try that. thanks.

---

