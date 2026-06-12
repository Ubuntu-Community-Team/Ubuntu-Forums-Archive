---
title: "Fed up with glib and atk.  Does libgtk2.0 include them?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by gomezj00 on 2006-06-20
Hi everyone,
after trying to install glib, atk, gtk, and pango, I'm fed up with the whole process.  Can someone tell me if the libgtk2.0 package includes glib, gtk, and everything else I'll need.  I'm trying to install a few compilers that rely on these packages and would just love to get to work sometime soon rather than have to fight with these packages.  Thank in advance for all your help.  I really do appreciate it!

---

### Post by Perfect Storm on 2006-06-20
Umm...what are you trying to do? You know you can grab them from synaptic, right?

---

### Post by gomezj00 on 2006-06-20
How so?  Do I just have to install the libgtk2.0 package or something?  I'm trying to setup Anjuta and it relies on these packages.  by the way, thanks for trying to help me out.

---

### Post by Perfect Storm on 2006-06-20
You find synaptic package manager in System Tab ---> Adminstration.
You'll find many of the stuff you need there and it's easy to install.
If you want to add extra to get more stuff check: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Anjuta is there, you just need to enable **universe** in your source list. Best way is to use the link I've show above.

Then open the terminal (Application tab ---> Accessories):
```
sudo gedit /etc/apt/sources.list
```
clean it and use the one provided by the link. Save and exit it. Then:
```
sudo apt-get update
```
It might complain but if you read the explaination in the link it's easy solved (adding some keys).
Then run sudo apt-get update again when solved the key thing.
Now open synaptic package manager and press the search button and search for Anjuta.

Bascially with synaptic you can install over 18000 applications/lib with a one or two click.

Edit: If you have any problems/question, don't hesistate to ask :)

---

