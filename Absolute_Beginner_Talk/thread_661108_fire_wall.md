---
title: "fire wall"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by javierr on 2008-01-07
hi!
does anyone know any tutorial for beginner in how setup my fire wall .. i just start using ubuntu 7.10.....

thank you !

---

### Post by tech9 on 2008-01-07
> **javierr said:**
> hi!
does anyone know any tutorial for beginner in how setup my fire wall .. i just start using ubuntu 7.10.....

thank you !

7.10 has a built-in firewall...

they are called IP Tables

you can install a front-end interface call firestarter

open terminal and type

```
sudo apt-get install firestarter
```

This can help you setup additional policies for allowing or blocking inbound/outbound connections, but it is not the firewall itself...

nevertheless, it's a nice tool, I use it

You can also view your connections from firestarter, see who you are connecting to and who is connecting to you.

---

### Post by Dr Small on 2008-01-07
Your firewall comes preinstalled on Ubuntu as iptables. To configure it with a graphical user interface, check out Firestarter ;)
```
sudo apt-get install firestarter
```

Then under System > Administration > Firestarter you should find where you can configure it.

Good luck!

Dr Small

---

