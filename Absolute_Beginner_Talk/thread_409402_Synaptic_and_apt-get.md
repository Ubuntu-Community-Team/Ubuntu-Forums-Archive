---
title: "Synaptic and apt-get"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-14
Am I correct in assuming that Synaptic is the GUI based application installer and apt-get is the terminal based? Is there a feature or another program that installeds software packages and then makes sure they meet all the dependencies and work properly.

---

### Post by Happy_Man on 2007-04-14
Well, from the command line, you could use aptitude. For example, instead of 

```

sudo apt-get install amarok

```

you use

```

sudo aptitude install amarok

```

There's no difference between the two installing,  but when you use aptitude to uninstall something, all its dependencies go away with it. I'm not sure which one Synaptic uses, though; most likely aptitude. Hope this helps!

---

### Post by Seisen on 2007-04-14
There is another one that called Gdebi that will do the same thing. This works if you download a .deb file and want to install it with a gui.

---

### Post by sailor2001 on 2007-04-14
also add/remove programs and ala carte

---

### Post by Maestro23 on 2007-04-14
Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

