---
title: "Ethernet not recognized"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by LostLake on 2007-10-23
I just installed gusty on a used computer i just purchased. I plugged in the cable from my router and no internet. I checked the network manager and there is no ethernet card recognized by ubuntu... Im lost...

---

### Post by Pumalite on 2007-10-23
Try adding 'irqpoll' to your kernel boot parameters.

---

### Post by LostLake on 2007-10-23
Im very new to this. how would i go about doing this?

---

### Post by Pumalite on 2007-10-23
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

---

### Post by GSF1200S on 2007-10-23
First off, post the contents of the following in a post, using the exact commands listed in a terminal. The first one is a file that names your network devices (ethernet card, wireless card) for your system. The second one is basically the network config file...

```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

-and-
```

sudo gedit /etc/network/interfaces
```

Im pretty sure I can get your ethernet to work automatically from bootup, and I can get it to work from the terminal, but getting the gnome network manager to work will be tough- im on KDE...

**Dont change anything.. You dont have to use "sudo," as that just gives you rights to write to important files...**

---

