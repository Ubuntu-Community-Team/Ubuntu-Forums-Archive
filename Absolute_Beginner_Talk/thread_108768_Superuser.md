---
title: "Superuser???"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by WackToMack on 2005-12-26
Hello everyone.  I need a little help, again.  I just installed Ubuntu 5.10 Breezy Badger on another HDD.  I'm gonna use this particular Ubuntu installation just to mess around with it... anyways, I just got Ubuntu installed and updated and I downloaded the newest Automatix .deb.  I used this code to install it :

```
dpkg --install automatix-ubuntu_4.0-1_i386.deb
```

When I use this code I get this message :

> dpkg: requested operation requires superuser privilege

What??? :confused:  I'm the only user on this OS.  How do I change my status to superuser???

---

### Post by silvagroup on 2005-12-27
In terminal enter:
sudo -s
I too am fairly new at this, you can also do sudo before your commands and enter password when it prompts for password, by the way you entered that when you did the install.

---

### Post by WackToMack on 2005-12-27
Thanks... I ended up using this code instead :

```
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

It worked... Thanks for the new code though... It'll come in handy.

---

