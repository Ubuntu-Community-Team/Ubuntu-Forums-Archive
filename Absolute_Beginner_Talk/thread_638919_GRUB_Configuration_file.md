---
title: "GRUB Configuration file"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-12-12
Hey,

I've forgotten the path to the GRUB config file. Can anyone help?


CosmicFlux

---

### Post by dstew on 2007-12-12
/boot/grub/menu.lst

---

### Post by ImALittleTeaPot on 2007-12-12
once you get to boot/grub/menu.lst ...how do you change a line in the file. I'm having a problem with booting up 7.10 (after install) and I've read on the forums that adding 'irqpoll' to the line 

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7eec31fb-03e9-40cd-861a-efe58a7aec56 ro quiet splash (irqpoll goes here)

will fix my problem. But when i try to add 'irqpoll' i get the message that i don't have the privelege to do so. Thought I was logged in as administrator but i guess not.

---

### Post by ImALittleTeaPot on 2007-12-12
NVM  fixed it with 

CODE:
gksudo gedit /boot/grub/menu.lst

---

### Post by CosmicFlux on 2007-12-13
OK, thanx!

---

### Post by markyb86 on 2007-12-13
what does gksudo do that sudo doesnt? i keep seeing it places

---

### Post by mcduck on 2007-12-13
> **markyb86 said:**
> what does gksudo do that sudo doesnt? i keep seeing it places

Offers you a GUI box for inputting the password, and most importantly, load's root's environment for graphical applications correctly which is something sudo doesn't do.

Using sudo for graphical applications can in some cases result in ownership of some of your own configuration files changing to root, making you unable to log in any more or change some of your own settings.

You should _always_ use gksudo (or kdesu in KDE) for graphical applications, sudo is only for command line.

---

### Post by A$h X on 2007-12-13
Is using sudo gedit acceptable, or should i use gksudo?

---

### Post by mcduck on 2007-12-13
> **A$h X said:**
> Is using sudo gedit acceptable, or should i use gksudo?

While Gedit doesn't seem to have this problem with 'sudo', it would be better (and also easier for you) to just learn the habit of using gksudo with _every_ graphical application, instead of trying to find out which ones work and which ones break ownership of your files if run with sudo..

So, I'd say that while using sudo with Gedit works, it's still not acceptable ;)

---

### Post by philinux on 2007-12-13
I sometimes forget to use gksudo with gedit and luckily not caused any probs.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

