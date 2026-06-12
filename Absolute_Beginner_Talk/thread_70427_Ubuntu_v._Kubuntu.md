---
title: "Ubuntu v. Kubuntu?"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by eric.stone on 2005-09-29
I have Kubuntu up and running on an AMD 64.  In the past I've used Red Hat Linux.  In Red Hat, I was able to select between KDE and Gnome sessions at log in.  Can this be done with Ubuntu and Kubuntu?

---

### Post by remin8 on 2005-09-29
Definately yes! if you installed Kubuntu from CD/whatever open kynaptic and select ubuntu-desktop. if you installed Ubuntu and want KDE open synaptic and get kubuntu-desktop! Its that easy!

---

### Post by ltmon on 2005-09-29
Yes,

> sudo apt-get install ubuntu-dekstop

is the command to get it.

Then gnome will be available a session type in your login screen.

L.

---

### Post by eric.stone on 2005-09-29
Just tried it,  got the following error msg:  

"E: Couldn't find package ubuntu-dekstop"

---

### Post by eric.stone on 2005-09-29
I found the reason for the error:  it's "desktop" v. "dekstop."  In the meantime, I'm trying kynaptic.  If it doesn't work, I'll run the apt-get install command you suggested.  Thanks much for the help.
Eric

---

### Post by Hobbsee on 2005-09-29
you'll probably find it's easier to use apt-get if you know the program name that you want - otherwise you can hit search in kynaptic, and get it that way too...or synaptic, if you decide to install that (it's one of the first things I install after firefox!)

---

### Post by eric.stone on 2005-09-29
Thanks much.  Kynaptic failed, but apt-get install worked like a champ the second time.  Now I've got KDE and Gnome up and running well.
Cheers from D.C.

---

