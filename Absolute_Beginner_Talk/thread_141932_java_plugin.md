---
title: "java plugin"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-09
hi, im a keen runescape player and i have finaly got around to trying it here on linux. however i need to use a java download/plugin. can any one help. i tried but for some reason i couldnt get it to work.

a note on the side: I find saving documents on ubuntu a real pain. i psose it takes time but hey

---

### Post by mlind on 2006-03-09
I suggest you install Sun's java environment. maybe easiest way to do this
using [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")

you can also create installable .deb package yourself using java-tools package.

---

### Post by yatesDELTA on 2006-03-09
uhm i am stuck. where do i download from?

---

### Post by mlind on 2006-03-09
see first post on that Automatix thread. There's section called "Installation
Instructions".

Those commands must be executed on terminal session. If you use
Gnome desktop environment, press ALT+F2 and write *gnome-terminal*
to open instance of terminal.

---

### Post by yatesDELTA on 2006-03-09
this is my first doing this kina stuff ever

---

### Post by mlind on 2006-03-09
[QUOTE=yatesDELTA]this is my first doing this kina stuff ever[/QUOTE]

you'll get the hang of this soon :)

Synaptic offers you graphical environment for managing your Ubuntu sofware.
apt-get & apt-cache are tools for doing synaptic stuff command line-driven.
dpkg -commands are more low-level package handling, usually you need these
for installing local .deb packages, like the automatix .deb you grabbed over the
internet using *wget* command.

you can compare .deb packages with windows .msi installer packages.

---

### Post by yatesDELTA on 2006-03-09
id prefer to use a graphic enviroment

---

### Post by Perfect Storm on 2006-03-09
[QUOTE=yatesDELTA]id prefer to use a graphic enviroment[/QUOTE]

Buut soon you'll get addicted to commands like the rest of us *[evilish dr. doom laughter]*Muwhahahaha*[/laughter]*

Seriously,
when you get to known linux/ubuntu a bit better you'll find commands a lot easier :)

If you wanna try to do some commands to install java, try this:

Open you terminal (Applications tab ---> Accessories ---> Terminal)
and type:
```
sudo gedit /etc/apt/sources.list

```

add the lines:
[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

Save it and exit it.
Now back to the terminal and type:
```
sudo apt-get update
sudo apt-get install sun-j2re1.5
```

Now it's install and ready :)

---

