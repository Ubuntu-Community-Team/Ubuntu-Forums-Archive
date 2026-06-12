---
title: "update manager dead.."
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Nevermore on 2006-10-24
I installed edgy yesterday, almost everything works, but the module for my laptop..
BUT
once i installed italian language update-manager stopped working, it does look for updates, but doesn't install anything..
how can i fix it?
Thanks

---

### Post by taurus on 2006-10-24
Are you using synaptic?  What happens if you check for update from a terminal, Applications -> Accessories -> Terminal?

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by Nevermore on 2006-10-24
seems that dbus is not performing correctly..

---

### Post by Nevermore on 2006-10-24
from cli everything works
but from gui not..
seems dbus is b0rked..
i issued sudo update-manager
and got this:
could not initialize dbus

---

### Post by taurus on 2006-10-24
I am not in front of my Ubuntu right now but see if you can reinstall dbus again using aptitude from a terminal!!!

---

### Post by Nevermore on 2006-10-24
tried to
sudo apt-get install --reinstall dbus
rebooted
but still error...

---

### Post by Nevermore on 2006-10-24
seems that even reinstalling dbus doesn't fix the problem..
it happened to me before and the only way was reinstalling, but after an upgrade the problem appeared again..
this time i am not gonna reinstall..

---

### Post by taurus on 2006-10-24
Stick with aptitude for now...

---

### Post by Nevermore on 2006-10-24
yep taurus
anyway today there are no updates..

---

### Post by taurus on 2006-10-24
> **Nevermore said:**
> yep taurus
anyway today there are no updates..
I usually run aptitude to check for updates maybe once or twice a week!  No need to check it every single day...  ;)

---

### Post by giuliastro on 2006-10-30
I confirm update-manager stopped working since upgrading to Edgy. I tells me there are new updates, but something goes wrong every time I want to install them. Using apt or aptitude to upgrade works every time.

---

