---
title: "new gnnks,ome"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-24
IS there a way I can install the new Gnome version without installing the entire dapper?
Because I really like the new look, but I don't want to upgrade to dapper again, my last experience wasn't very succesfull...

Is it possible?
Tha

---

### Post by Mr Fat Bat on 2006-05-18
I'm sure you could always compile and install it yourself from the Gnome Download Page:

[http://www.gnome.org/start/2.14/]("http://www.gnome.org/start/2.14/")

I'm not 100% sure if there are any repositories where you can download it from, hopefully with this bump somebody can answer that for you!

Good luck ;)

---

### Post by Sef on 2006-05-18
> IS there a way I can install the new Gnome version without installing the entire dapper?
Because I really like the new look, but I don't want to upgrade to dapper again, my last experience wasn't very succesfull...

Is it possible?
Tha

Without installing Dapper may break your system.  So be careful.

If you're using Breezy and want to update to Dapper, try this from the terminal

sudo apt-get update

sudo apt-get dist-upgrade

That will get you Gnome 2.14.1

Warning:  **Back up** your data first.  Also make sure you have an install disk.  Sometimes the dist-upgrade can break your system.  Usually not, but it can happen.

---

