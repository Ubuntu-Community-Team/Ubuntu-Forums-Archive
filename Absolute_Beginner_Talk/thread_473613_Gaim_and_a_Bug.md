---
title: "Gaim and a Bug"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-06-14
Does anyone else have this problem? I'll be chatting to a specific friend, and then it just closes...but with other online friends this does not happen? What is going on?

---

### Post by farueulogy on 2007-06-14
Not heard of it - But when in doubt, upgrade.
[B]
Warning - There might be better advice out there, I'm still new and not sure if this is the way I installed Pidgin (new name for Gaim).[/B]
*Information from: [http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn]("http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn")*

Gaim is now Pidgin.

To install, open terminal

> $ cd /etc/apt/
> $ gedit sources.list

This will open a text document, copy and paste the following at the end of it, **save your changes**:

> deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse

Close the document and return to the terminal and enter:
> $ sudo apt-get update
(It will ask for you password)

Then enter:
> $ sudo apt-get install pidgin 

---

