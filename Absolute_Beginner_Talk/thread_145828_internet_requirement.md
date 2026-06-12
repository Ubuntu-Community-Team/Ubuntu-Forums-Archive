---
title: "internet requirement?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by xubuntux on 2006-03-17
Do most of the programs in the administration menu need internet connection?
I just finished installing ubuntu and have been able to login.. yay! Checked out some programs and they worked fine(I checked out the media players and games :mrgreen:) However when I tried opening the ones in the administration module they seem to load up but dont appear. I havent setup the internet connection yet so I was thinking that this might be the cause... Can somebody point me to the right direction? thanks!

---

### Post by meborc on 2006-03-17
no, you don't need an internet connection to use your computer...

you need internet connection to upgrade and install new programs via apt-get, but i can't imagine that anything in system menu would need it...

it seems to me that there is smthing wrong with your setup, if the administrator menu is not working... be aware though that most of the things there will prompt you for your password... but if you don't see the box... :-k

---

### Post by poofyhairguy on 2006-03-17
[QUOTE=xubuntux]Do most of the programs in the administration menu need internet connection?[/QUOTE]

Nope. Just the correct password!

---

### Post by steve.horsley on 2006-03-17
Does a box pop up and ask for a password when you select something in the admin section? It should do.

Assuming it doesn't, can you open a comand prompt (Accessories->Terminal) and tell us what happens with the following two commands:
> gtksudo synaptic
sudo ls
Posting the output from the command window would be good.

---

