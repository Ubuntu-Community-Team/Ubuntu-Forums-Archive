---
title: "Plase help me"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by catch2two on 2007-08-03
I posted further down this page i just want my comp to work again i cant update add/remove or use synaptic :

If i click on the orange square update i get this:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Id i go into synaptic and try and remove contacts i get this:

E: contacts: subprocess post-removal script returned error exit status 139

and it is highlighted in red.

I was very happy with my system but now it sucks

---

### Post by aquavitae on 2007-08-03
Did you try "sudo apt-get install -f"?

---

### Post by kyphi on 2007-08-03
You obviously have had a lot of fun doing things in Ubuntu.  Somewhere along the way you must have damaged a few files so now your system does not work anymore.

To fix it would be difficult because no-one knows just what you have done and you, probably, do not remember the chain of events.

Most people when they first embrace Ubuntu have travelled along the same path of experimenting, breaking, not knowing how to fix it.  That is what lessons are made of.

There is only one way to get your Ubuntu back: Start from the beginning and reinstall.

---

### Post by Alexander2007 on 2007-08-03
> **catch2two said:**
> I posted further down this page i just want my comp to work again i cant update add/remove or use synaptic :

If i click on the orange square update i get this:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Id i go into synaptic and try and remove contacts i get this:

E: contacts: subprocess post-removal script returned error exit status 139

and it is highlighted in red.

I was very happy with my system but now it sucks

Open a terminal window and type:```
 sudo apt-get install -f
```

---

### Post by Alterax on 2007-08-03
Looks like the uninstall script for the contacts package is broken.  It happens, no big deal.
Try this:

sudo dpkg -P contacts
(This not only tries to uninstall the corrupt "contacts" package, but removes it completely)
(The -P means PURGE, if that helps)

then the other command you were given

then try to rebuild your installation

sudo apt-get update 
sudo apt-get dist-upgrade

This should handle it.

--Alterax

---

