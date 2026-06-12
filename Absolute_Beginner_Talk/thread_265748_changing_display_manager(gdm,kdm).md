---
title: "changing display manager(gdm,kdm)"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-09-26
i ma currently using kde display manager(kdm) as my default display manager. i want to use gnome display manager now. how to set gdm as default display manager.

---

### Post by bluefrog on 2006-09-26
something like
sudo dpkg-reconfigure ubuntu-desktop
should ask you at the end of the reconfigurationwhat manager you want to use.

James

---

### Post by Bachstelze on 2006-09-26
sudo dpkg-reconfigure gdm

---

### Post by whizbaby on 2006-09-26
On your login screen (where you type username and password) there is a button *session*. Hit it and choose *gnome* and hit *change session*. After entering your username and password you will be asked if you want gnome to be default or only login for one session. (Of course gnome needs to be installed for this)

---

### Post by Bachstelze on 2006-09-26
Display Manager != Desktop Environment...

The Display Manager is the login screen (and all that's behind).

---

### Post by whizbaby on 2006-09-26
Aah, o.k. I thought it was a session-changing matter (never used kdm). What are differences of kdm/gdm?

---

