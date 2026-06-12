---
title: "Frozen Mouse"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by oneofone2007 on 2007-04-25
New Ubuntu and linux user here, just got Feisty up and i'm loving it. Only one issue, every now and then, whether cause of Beryl or what i'm not sure, my mouse cursor locks up entirely. Everything continues to run fine, but the mouse is completely non-functioning. 


Any ideas?

---

### Post by bloodniece on 2007-04-25
I get that too. Usually I can unplug and plug back in the mouse and get it back.  But Beryl might be taxing your system too much.

---

### Post by oneofone2007 on 2007-04-25
> **bloodniece said:**
> I get that too. Usually I can unplug and plug back in the mouse and get it back.  But Beryl might be taxing your system too much.

Surely not. Its a AMD X2 4200, 1 1/2gb of pc3200, and an geforce 6600fx (512mb, pcie).

---

### Post by Cypher on 2007-04-25
I had the same thing happen to me on my Feisty installation, in both KDE and GNOME, but I found a fix for it online, see if it also works for you.
```

gksudo gedit /etc/modprobe.d/blacklist

```
Change this:
```

blacklist usbmouse
blacklist usbkbd

```
to
```

#blacklist usbmouse
#blacklist usbkbd
blacklist usbhid

```

Save, reboot and see if things get better..

---

### Post by poper on 2007-05-18
> **Cypher said:**
> I had the same thing happen to me on my Feisty installation, in both KDE and GNOME, but I found a fix for it online, see if it also works for you.
```

gksudo gedit /etc/modprobe.d/blacklist

```
Change this:
```

blacklist usbmouse
blacklist usbkbd

```
to
```

#blacklist usbmouse
#blacklist usbkbd
blacklist usbhid

```

Save, reboot and see if things get better..
Thanks Cypher, I've got the same problem than oneofone2007 so I've tried your fix, unfortunately it doesn't work me. It seems to reduce the number of times my mouse freezes, but it goes "crazy" sometimes (the pointer changes its position suddenly, buttons are "pressed" (without touching them!) and so on)

---

