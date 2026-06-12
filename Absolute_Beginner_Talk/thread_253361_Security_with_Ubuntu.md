---
title: "Security with Ubuntu"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-09-08
I'm not finding a secuity tab in Ubuntu. Is there a way to activate security settings or a firewall?

---

### Post by bluefrog on 2006-09-08
if you want gui, install firestarter (for example) other wise you need to use command line.

Now if you want to activate the firewall just because it is what is done when using windows, there is no need.

If you need it because of certain specs of your machine/program, well ok go on...(firestarter, firehol...)

James

---

### Post by xyz on 2006-09-08
In Synaptic, search and install "firestarter" or in a console:
```
sudo aptitude install firestarter
```

---

### Post by mtn on 2006-09-08
Firestarter is a firewall GUI, though as far as I am lead to believe there is a command line firewall installed by default.

With Synaptic (Applications>Add/Remove) install Firestarter and then start it up from the Applications>Internet menu.

---

### Post by mtn on 2006-09-08
bluefrog why is there no need? (I'm not techy, just struggling through)

---

### Post by jmtjet on 2006-09-08
I'm sitting behind a router, so I probably don't need a firewall-correct? What about anti-virus software like F-Prot. Do I need it or not? Do any of you people use AV software?

---

### Post by xyz on 2006-09-08
[http://www.ubuntuforums.org/showthread.php?t=136064&highlight=install+avg](http://www.ubuntuforums.org/showthread.php?t=136064&highlight=install+avg)

[http://www.ubuntuforums.org/showthread.php?t=250188&highlight=anti+virus](http://www.ubuntuforums.org/showthread.php?t=250188&highlight=anti+virus)

should enlighten you on the subject.

---

### Post by bluefrog on 2006-09-08
if you are networking with windows machine, you may eventually install an anti virus to check files you may forward to the *dows pc. As you are already behind a router, the need for a firewall is definitely equal to none.

By default a ubuntu desktop have no open ports so no need to firewall any ports.

I am not a security expert but after having switch totally to linux 1 year and a half and having no firewall nor AV on my machine, I have a tendancy to believe I am pretty much safe.

I understand that expert people could certainly do what they want with my machine especially since I installed ssh, apache and other goodies but well let's face it, I have nothing important on my computer (e.g: never keep your credit card number on your machine - whatever system it is). website and other stuff are backed up. takes me 2 minutes to restore an image if one day my pc goes down for whatever reason.

From time to time I run chrootkit to "reassure" myself.

ah of course people could use my machine to run some attacks on the net...

James

---

