---
title: "How to configure startup"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by alaniane on 2007-08-06
I want to configure Ubuntu to startup in text mode instead of gui.   I remember there is a setting in the startup files that I can change; I just can't remember which startup file and where it is located.  

I have made the change before on Redhat Linux version 7.0; however, it has been a while ago.

---

### Post by Rocket2DMn on 2007-08-06
You need to edit /etc/inittab.  Please back it up first, just in case...
```
sudo cp /etc/inittab /etc/inittab.backup
gksudo gedit /etc/inittab
```
then modify the line 
"id:5:initdefault:" to "id:3:initdefault:"
This will change your default init level to runlevel 3 (multi-user CLI), rather than runlevel 5 (multi-user GUI).
You can always change the runlevel on the fly by using the "init" command, like
```
init 5
init 3
```

---

### Post by alaniane on 2007-08-06
Thank you.

---

