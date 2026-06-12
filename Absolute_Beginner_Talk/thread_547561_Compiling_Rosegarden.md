---
title: "Compiling Rosegarden?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by studley1728 on 2007-09-10
Forgive me for my absolute lack of knowledge on anything to do with Linux at all. I only started using it last week, when one of my teachers asked me to install Ubuntu on one of the computers in his lab. Since then he has asked me to put Rosegarden on here for one of his students, but I don't really know what to do. I downloaded it, obviously, but I don't know anything about compiling. Could anyone possibly offer me any help?

Thanks,
Cait

---

### Post by Perfect Storm on 2007-09-10
You can get Rosegarden through synaptic/apt-get/aptitude so you don't have to compile it (if you don't want to).

```
sudo aptitude install rosegarden
```
by command

---

### Post by studley1728 on 2007-09-10
I tried that, but when I searched for it I didn't get any results. :(

---

### Post by Perfect Storm on 2007-09-10
It's beccause you need to set up your sourcelist to get access to universe and multiverse. It will give a huge access to alot of stuff.

You can manually edit the list by;

```
sudo nano /etc/apt/sources.list
```



There's a source generator here: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by meindian523 on 2007-09-10
Or the GUI method is to go to Synaptic,System>>Administration>>Synaptic,

Settings>>Repositories.
Tick universe(2nd button).close and click reload.

Now you will find rosegarden on search.:)

---

