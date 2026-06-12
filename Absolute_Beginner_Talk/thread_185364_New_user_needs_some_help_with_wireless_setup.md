---
title: "New user needs some help with wireless setup"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Melcar on 2006-05-31
I have been trying to get an WPC54G v.2 card to work with an old dell laptop running Ubuntu 5.10.  After reading several of old threads on similar issues I was able to get it to work.  Unfortunatly I use WPA for my home network and I'm having a hell of a time trying to get WPA to work with the card.  I already tried using the WPA supplicant, but when I try to install it I keep receiving a "could not find package" message.  So I downloaded the package to the desktop, but now I don't know how to extract it.  Any help?

---

### Post by ubuntuuser on 2006-05-31
I can't help you with WPA in general, but to install any package you downloaded, type ```
sudo dpkg -i packagename.deb
```Good luck :D

---

### Post by deja2004 on 2006-05-31
Of course there's always:
```
sudo apt-get install wpasupplicant
```
Give that a go.

---

