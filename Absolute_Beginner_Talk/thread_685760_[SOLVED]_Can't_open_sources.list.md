---
title: "[SOLVED] Can't open sources.list"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-02-02
K. So here it is.

```
sudo gedit /etc/apt/sources.list
```

asks for password and nothing happens.

I've tried googling it to no avail. 

```
gksudo gedit /etc/apt/sources.list
```

gives me.

> (gedit:26108): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I'm terribly confused.

---

### Post by ssharps711 on 2008-02-02
Edit: Minus the smiley. lol its an "8" and ")"

---

### Post by raptir on 2008-02-02
Can you view the file if you run it without sudo?

```
gedit /etc/apt/sources.list
```

---

### Post by jose158 on 2008-02-02
Try this: ```
gksudo nautilus
``` and then navigate to the sources.list and open it. :)

---

### Post by ssharps711 on 2008-02-02
K. Nm I just shut down and it's working fine now. Must have had something open that wasn't supposed to be probably "GnomeUI-WARNING **: While connecting to session manager:"

Thx

---

