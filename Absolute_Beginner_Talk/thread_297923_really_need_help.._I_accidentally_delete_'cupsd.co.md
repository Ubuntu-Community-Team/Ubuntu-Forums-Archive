---
title: "really need help.. I accidentally delete 'cupsd.conf'"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by pen-c on 2006-11-11
I'm using the Edgy eft, and was trying to install cups-PDF to my system.
But instead of editing "/etc/cups/cupsd.conf" file, i accidentally deleted it.
And it seems to me that it's an important file that other apps rely on it.

Is there a way to fix this?? 
please help...

---

### Post by taurus on 2006-11-11
What if you remove cupsd and reinstall it again?

```

sudo aptitude update
sudo aptitude remove cupsd
sudo aptitude install cupsd

```

---

