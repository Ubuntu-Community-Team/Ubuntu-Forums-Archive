---
title: "Can't log in a root!"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by hazza_21 on 2005-07-02
Hi,
When I boot up and try and log in as "root" it tells me that the administator canot log in on this screen.  So where can i log in!  I can log in a normal non admin user but this isn't what i want!

When repling try and remeber I am very new to this and have little knowledge of linux!

---

### Post by aysiu on 2005-07-02
Two things here.

First of all, why do you want to log in as root? What do you want to accomplish? Believe it or not, depending on the situation, it may be easier to use a *sudo* command. Most likely, anything you want to do is outlined in the [Ubuntu Guide](http://www.ubuntuguide.org).

Okay, now... assuming that you really do have a need to log in as root temporarily, if you go to login screen setup, there's one of the tabs that has an option in it "allow root to log in." Check that box. Then, you have to change the root password in the user setup.

If that sounds too difficult, just type *sudo nautilus* in the terminal, and you can navigate the directories as root temporarily.

Again, it really depends on what you're trying to accomplish. What do you want to do? You don't, for example, have to log in as root to install software.

---

### Post by hazza_21 on 2005-07-02
[QUOTE=aysiu]Two things here.

First of all, why do you want to log in as root? What do you want to accomplish? Believe it or not, depending on the situation, it may be easier to use a *sudo* command. Most likely, anything you want to do is outlined in the [Ubuntu Guide](http://www.ubuntuguide.org).

Okay, now... assuming that you really do have a need to log in as root temporarily, if you go to login screen setup, there's one of the tabs that has an option in it "allow root to log in." Check that box. Then, you have to change the root password in the user setup.

If that sounds too difficult, just type *sudo nautilus* in the terminal, and you can navigate the directories as root temporarily.

Again, it really depends on what you're trying to accomplish. What do you want to do? You don't, for example, have to log in as root to install software.[/QUOTE]
 I want to change the grub boot list.  I have found the file and how to do it but can't touch it as root is the only one who can.
I will read the guide as I am pretty useless @ this.
Thanks.

---

### Post by aysiu on 2005-07-03
[QUOTE=hazza_21]I want to change the grub boot list.  I have found the file and how to do it but can't touch it as root is the only one who can.
I will read the guide as I am pretty useless @ this.
Thanks.[/QUOTE] You'll probably want this part of the guide, then.
[http://www.ubuntuguide.org/#addwindowsentrygrubmenu](http://www.ubuntuguide.org/#addwindowsentrygrubmenu)
Some people are afraid of the command line, but you can really just cut and paste these commands in--you don't have to understand what they mean.

---

