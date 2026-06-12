---
title: "Mouse single/double click (in sudo mode)"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2006-07-15
Hi I have set my mouse for double-click to open files etc, but I am unable to set the root settings.  When I > sudo konquerorthe mouse clicks revert to single click.

Any ideas ?

---

### Post by someusernoob on 2006-07-15
Do:

```

kdesu konqueror

```

This will open konqueror with root permissions, but also with the root configuration files (other then sudo, which opens with root permissions, and your configuration files)! You have to change the double click setting tho, but only once, settings will be stored under the root account now, where its supposed to be stored.

For more detailed information: [http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

---

### Post by infoseeker on 2006-07-15
Thanks for the reply but there is no setting for single/double click files in konqueror, only for underlining files.  System settings (Control Centre) sets mouse single/double clicking.

EDIT : Found out eventually :D

> sudo kcontrol :D
That sorted it out :)

---

