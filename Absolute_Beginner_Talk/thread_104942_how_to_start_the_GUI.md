---
title: "how to start the GUI"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by prete on 2005-12-17
i'm am a new linux user and i'm having some trouble with ubuntu.

I want to know how to start the GUI. In mandrake (witch i used before ubuntu) i would start automaticley or else i could use the "start x" command. How do I start it in Ubuntu. I use Ubuntu 5.04 for Intel x86.

---

### Post by Rackerz on 2005-12-17
Did you install Ubuntu using the 'server' option, if you did then there is no GUI. If you installed normally then you should type; startx 

You will probably get errors, but if not your GUI should have started! :D

---

### Post by bscbrit on 2005-12-17
If you do get errors try the following:

sudo apt-get install gdm

That should install the gnome display manager and all of its dependencies.  You should then have a working GUI I think!

(Of course, I could be wrong, we are all, experts and novices alike, still learning...)

---

### Post by xmastree on 2005-12-17
It should start automatically, which suggests that something went wrong with your installation. Try **startx** but expect to see some errors. Those errors should help you diagnose the problem.
If you can't figure out what's wrong, search these forums for those errors. Chances are, someone already had that problem and the answer is here somewhere.

---

### Post by NotJustANewbie on 2005-12-17
Remember to start gdm once it is installed too.
```
/usr/sbin/gdm start
```

---

