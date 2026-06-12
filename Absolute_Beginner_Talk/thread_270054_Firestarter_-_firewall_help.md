---
title: "Firestarter - firewall help"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-10-02
Ok so I have setup a firewall on my Ubuntu computer with firestarter but I want to know, do I have to start firestarter from the "Applications" menu on every startup or does it start automaticly and I just can't see the Icon in my tray until I click on it from the "Applications" menu?

Thanks for the help.

---

### Post by uk_sphinx on 2006-10-02
from what i learned today firestarter is a graphical way for you to set the port preferences.
i think its running under ip tables
its also a easy way for you to monitor the logs.

---

### Post by charles.g.moore on 2006-10-02
I believe it's running upon startup, you could maybe do an nmap on your LAN to see if it's hiding the ports...

Im not much of a Network guru but I know that when I start my sys up I cant ssh unless the hole is there...

---

### Post by PPAAUULL on 2006-10-02
Ok Thanks I think I figured it all out.

---

### Post by charles.g.moore on 2006-10-02
Go here and check to make sure that your ports are all hidden
[http://www.grc.com/default.htm](http://www.grc.com/default.htm)

and try it as soon as you restart...

Look for the shields up link

---

### Post by PPAAUULL on 2006-10-02
Weird but even when I go to Firestarters menu and "Disable" the firewall, the test claims that alll the ports are stealth.
Shouldn't it atleast get one that isn't?

---

### Post by bulldog on 2006-10-02
> **PPAAUULL said:**
> Ok so I have setup a firewall on my Ubuntu computer with firestarter but I want to know, do I have to start firestarter from the "Applications" menu on every startup or does it start automaticly and I just can't see the Icon in my tray until I click on it from the "Applications" menu?

Thanks for the help.


Try to put the firestarter command in your sessions menu for autostart.
You will have the icon then
```
gksudo firestarter
```in your sessions menu.

---

### Post by PPAAUULL on 2006-10-02
Thanks

---

