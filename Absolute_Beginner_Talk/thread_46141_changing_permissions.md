---
title: "changing permissions"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by beamo on 2005-07-03
I am trying to give my username write permissions outside of the home directory but can't seem to get it to work. I am the only user on my computer and will be for the foreseeable future.

How can I do that? Thanks.

---

### Post by sapo on 2005-07-03
[QUOTE=beamo]I am trying to give my username write permissions outside of the home directory but can't seem to get it to work. I am the only user on my computer and will be for the foreseeable future.

How can I do that? Thanks.[/QUOTE]

you need to use sudo to that:

sudo chmod 777

or sudo chmod +w

or you can change the owned with: sudo chown newuser folder/files

sudo will ask a password.. just type your user password on it  :grin:

---

