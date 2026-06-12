---
title: "Can I go back to Gnome without a lot of trouble?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by geek_overlord on 2007-10-03
Ok, I finally got Feisty installed with KDE however I'm thinking it might be best to go back to Gnome. Not that I don't like K however I'm still a noob and it seems like there is a lot more documentation and help for the Gnome environment. So my question is " will it be a big fuss to switch? Will I need to wipe my drive and start from scratch? Man I had enough trouble just getting the $#!$ network up and running. That one issue is enough to stop me in my tracks. So how is such a thing accomplished? Thanks in advance for your help.

---

### Post by tdrusk on 2007-10-03
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install ubuntu-desktop
```

switch to ubuntu
```

sudo aptitude remove kubuntu-desktop
```

simple as that.

If you want to keep kubuntu, don't do the last command.

---

### Post by bobplano on 2007-10-03
do you already have gnome installed and you installed kde or did you install kubuntu? you can just do 
sudo apt-get --purge kubuntu-desktop

or install gnome first and then gett rid of kubuntu

sudo apt-get install ubuntu-desktop

---

### Post by ryanVickers on 2007-10-03
yesh, ```
sudo apt-get install ubuntu-desktop
``` should add gnome - you can then pick it before you logon from the sessions menu

---

### Post by geek_overlord on 2007-10-03
WHOA. No wonder why I want to switch back. This is one blazin fast forum. I did a full install with Kubuntu. So which one of these should I do?

---

### Post by bobplano on 2007-10-03
do fuzzyhair's commands

> 
Code:
```

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install ubuntu-desktop

```
switch to ubuntu
Code:
```

sudo aptitude remove kubuntu-desktop

```
simple as that.

If you want to keep kubuntu, don't do the last command.
__________________

---

### Post by ryanVickers on 2007-10-03
mine is good :)  I'll just install gnome - the others involve removing kde and upgrades to nothing and that stuff, but if you want to do all that, they are perfectly good responses too :p

---

### Post by alienexplorers on 2007-10-03
Getting back to pure gnome:
> [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

### Post by tdrusk on 2007-10-03
> **alienexplorers said:**
> Getting back to pure gnome:

amen

I have used that guide SO many times.

---

### Post by geek_overlord on 2007-10-03
It looks like the method Ryan described worked like a charm. Thanks to everyone for your help.

---

### Post by ryanVickers on 2007-10-03
Yes!:guitar:

You know your a real geek when you end up in a speed race to list the best way to remove and install Linux desktop environments! :lolflag:

---

### Post by tdrusk on 2007-10-03
> **ryanVickers said:**
> Yes!:guitar:

You know your a real geek when you end up in a speed race to list the best way to remove and install Linux desktop environments! :lolflag:

been there done that :P

Threadstarter, please go to the top of the thread, click thread tools, and mark the thread as solved.

---

