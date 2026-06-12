---
title: "Konqueror root access"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-08-02
Is there anyway to get Konqueror to login as root in ubuntu (I am not using kubuntu)?

This way I don't always have to login into the terminal and login as root to manipulate/run files in the root directory.

---

### Post by tennisplaya05 on 2007-08-02
well, i know the programmers made it that way for a reason, (so you don't accidently screw up your system). But if you're constantly going in and out of root konqueror, i feel for you. I think i remember seeing an add on to konqueror that was just a small button in the window that switches you in and out of superuser. I'll do some searching for it :)

---

### Post by tennisplaya05 on 2007-08-02
i was just thinking, as a temporary fix, why not just do something along the lines of:

creating another konqueror panel button, then configuring it, then going over to the application tab, changing the current command to sudo konqueror, then checking run in terminal under advanced options? This will basically give you rot privileged konqueror with the touch of a button, (only downside being that terminal will also open with it)

---

### Post by tennisplaya05 on 2007-08-02
oh wow, i think i misread your original question. 
just try 

sudo konqueror.

---

### Post by B-777 on 2007-08-02
> **tennisplaya05 said:**
> oh wow, i think i misread your original question. 
just try 

sudo konqueror.

No go I am afraid...also tried gksudo with no luck.

---

### Post by aysiu on 2007-08-02
It's ```
kdesu konqueror
``` Do not use *sudo* with graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I believe if you install *konq-plugins*, you should be able to have an *Edit as root* context menu item in Konqueror, too.

---

### Post by tennisplaya05 on 2007-08-03
wow, i never realized the effects of sudo could be so adverse. 
thanks for enlightening, aysiu

---

### Post by Brunellus on 2007-08-03
> **tennisplaya05 said:**
> wow, i never realized the effects of sudo could be so adverse. 
thanks for enlightening, aysiu
*nix system permissions are there for a reason.  We trifle with things outside /home at our peril.

---

### Post by Nekiruhs on 2007-08-03
> **tennisplaya05 said:**
> wow, i never realized the effects of sudo could be so adverse. 
thanks for enlightening, aysiu
Yeah, I lost sudo privs one time when I did sudo gedit. I had to boot to recovery mode to fix it.

---

