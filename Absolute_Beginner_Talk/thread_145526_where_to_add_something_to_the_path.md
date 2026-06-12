---
title: "where to add something to the path"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by chadmichael on 2006-03-16
Hello.  I interested in where the preferred place to add something to the path should be.  There are several file choices.  I would like to hear people's opinions on the various choices.  I used to use Suse and it seemed to have its own preferred conventions.  Does Ubunut?  Where do these conventions come from?

By the way, I'm adding java to the path.  So its something that should be system wide.

---

### Post by mlind on 2006-03-16
I usually need modified $PATH on terminal sessions only, 
so I put my entries on ~/.bashrc

I'm actually interested what's the preferred ways to set system wide variables on
Ubuntu. I've used only ~/.gnomerc, but It applies on Gnome sessions only.

Well, there's /etc/profile too.


/edit
doh, I meant .gnomerc

---

### Post by chadmichael on 2006-03-16
I changed some environment variables in /etc/profile and they work when I log in to a console directly.  However, when I go in to the graphical login, they don't seem to be set.  Does the graphical login not call the /etc/profile script?  THis is kind of a mess if so.

---

### Post by mlind on 2006-03-16
PATH variable is initialized on /etc/environment and it's read after /etc/profile

try to set your path on /etc/environment. It will affect to all users then.

---

### Post by chadmichael on 2006-03-16
Is /etc/environment a linux/unix convention or a ubuntu thing?

---

### Post by mlind on 2006-03-16
I guess it's a debian convention. I've only used the file for locale settings.
Locale settings on Fedora fedora are specified on /etc/sysconfig/i18n

---

