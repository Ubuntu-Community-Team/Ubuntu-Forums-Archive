---
title: "sudo and root terminal"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by halfvolle melk on 2005-09-04
I've noticed that "sudo" can't do all and that "su" log-in is sometimes required to do stuff. I've also noticed that "root terminal" merely requires my normal user pwd to become root. Or is this just a fake terminal that simulates "sudo"?

---

### Post by poofyhairguy on 2005-09-04
[QUOTE=halfvolle melk]I've noticed that "sudo" can't do all and that "su" log-in is sometimes required to do stuff. I've also noticed that "root terminal" merely requires my normal user pwd to become root. Or is this just a fake terminal that simulates "sudo"?[/QUOTE]

Hello. Here is a fun fact.

In Ubuntu there is a graphical sudo. Synaptic and this root terminal use it by default. You can use it too.

Open the terminal. Type this:

> gksudo nautilus

You now have a nautilus as powerful as you can get! (be careful with that)

That root terminal is a regular terminal with gksudo. So no root account is used.

---

