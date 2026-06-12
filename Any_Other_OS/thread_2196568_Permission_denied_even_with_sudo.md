---
title: "Permission denied even with sudo"
date: 2013-12-30
forum: Any Other OS
---

### Post by JanWolf90 on 2013-12-30
Hey everyone,

I'm currently working with contikios [([http://en.wikipedia.org/wiki/Contiki](http://en.wikipedia.org/wiki/Contiki))]("http://en.wikipedia.org/wiki/Contiki") where exists a command "motelist" which should give me a list of all motes(devices) connected. Now if I type

```
make motelist
```

I get a permission denied error (even though it shouldn't). So I tried

```
sudo make motelist
```

but I still get a permission denied error. When I try this command with a newer version of contiki (it's just another directory/folder) it works fine but I need it to work for the the older version. I think I somehow messed up something but I don't know what. Hopefully someone has an idea :)

Greetings,
Jan

---

### Post by Frogs Hair on 2013-12-30
***Moved to Other OS/Distro Support ***

---

### Post by thatredbird on 2013-12-30
Have you tried chmod to take possession, instead?

---

### Post by JanWolf90 on 2013-12-30
no since last time I used it I somehow messed up and had to reinstall ubuntu^^ so I guess I have to chmod of the whole contiki. Which mods should I use? chmod 555 /home/usr/contiki?

---

