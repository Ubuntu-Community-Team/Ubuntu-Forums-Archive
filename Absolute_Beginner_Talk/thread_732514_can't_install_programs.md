---
title: "can't install programs"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-23
I have a problem whenever i try to use ubuntu package installer program it gives me this message

only one software management tool is able to run at a time

please close other applications e.g. update manager, aptitude, synaptic 

I searched but can't find any program like these on, i even restarted my computer but got the same reading

---

### Post by RyviusRan on 2008-03-23
does anyone know a way to shut this mysterious program down that i can't seem to find

---

### Post by Oldsoldier2003 on 2008-03-23
> **RyviusRan said:**
> does anyone know a way to shut this mysterious program down that i can't seem to find

you could try

```
killall synaptic
killall aptitude
killall update-manager
```

But i think that thats really not the issue at hand, I'm looking to see if I can find another resolution for the issue. If it pans out I'll post in a couple minutes.

---

### Post by Oldsoldier2003 on 2008-03-23
My initial thought is you may have a stale lock... try looking in /var/lock and 

```
sudo rm /var/lock/aptitude
``` or whatever installer has a lock file left in there. be sure that you arent running a automatic update though.

---

### Post by RyviusRan on 2008-03-28
I still have the error even trying what was told. now when I use the terminal to try to install something i get this message....

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

anyone know what to do?

---

### Post by ramjet_1953 on 2008-03-28
Hi, there!

Just do what it tells you!

ie Type in a terminal:

[COLOR="Red"]sudo dpkg --configure -a[/COLOR]

Regards,
Roger :cool:

---

