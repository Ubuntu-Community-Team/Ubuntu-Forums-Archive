---
title: "[SOLVED] Error updating"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by befana on 2008-01-10
Hi!
I've just installed Ubuntu 7.10 on my Toshiba Satellite L40 14F with Vista. 
While updating linux-image-2.6.22-14-generic, I get this error:

E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb: corrupted filesystem tarfile - corrupted package archive

What that means and how to correct it?

---

### Post by Blutack on 2008-01-10
It means the package got corrupted whilst being downloaded.  It's rare but occasionally happens due to network interferece, that kind of thing.  To fix it, open a terminal and run

> sudo apt-get clean

to remove your cached .deb files.
and then

> 
sudo apt-get update
sudo apt-get upgrade

to update your package lists and then upgrade.

---

### Post by befana on 2008-01-10
Blutack,
thank you for your reply.
But few minutes after posting here I was trying to install Alltray via Synaptic. I've added repository for it, and I got an other error message. Meanwhile the language support on my Ubuntu does not want to start - it just stops, so, as my Ubuntu installation is not in english, I can not write here the exact new error I got, but it is something like this (hope you will understand): 
A bad formated row 80 in the source list /etc/apt/sources.list (distribution analysis). 

I got this error with Synaptic and with terminal, when typing sudo apt-get update.

---

### Post by Blutack on 2008-01-10
Delete the repository line you have added.
The warning means the line you added is not in the correct format for apt to understand, make sure it looks like the other lines and there is no break halfway through.
Synaptic has alltray by default, just make sure all software sources are enabled and search for alltray.

---

### Post by befana on 2008-01-10
Thank you, Blutack!
Almost everything with my Toshiba now is OK.

---

### Post by Blutack on 2008-01-10
No problem.

---

