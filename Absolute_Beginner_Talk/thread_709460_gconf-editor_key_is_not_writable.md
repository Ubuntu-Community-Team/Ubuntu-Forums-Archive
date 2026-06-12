---
title: "gconf-editor key is not writable"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by scales on 2008-02-27
hi all.  well at one point in time i was able to uncheck and check the can_suspend and can_hibernate boxes, but now for some reason i cannot uncheck them and when i try to run gconf-editor as root, (sudo su) i get the following
(gconf-editor:9128): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
any suggestions?

---

### Post by wolfen69 on 2008-02-27
**sudo** gconf-editor

---

### Post by scales on 2008-02-27
i tried that, i am not sure it will allow me to edit it as root....or it doesnt seem to make a difference

---

### Post by spd106 on 2008-02-27
It can be a funny old thing the gnome "registry".

A lot of it's settings are user-dependent, so you can't access them as root (and it's gksudo).

If you can't modify a key through the gconf-editor, then you can also try the terminal based gconftool or even edit the xml files directly under ~/.gconf or ~/.gnome2

NB It's not really a good idea to go messing around in there because you could break the user's profile. So at least create another (admin) user first, just in case.

---

