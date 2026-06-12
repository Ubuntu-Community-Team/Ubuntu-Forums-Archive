---
title: "Newbie question  on org.conf"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by CharlieRC on 2007-04-30
I am trying to add an entry to the file /etc/x11/org.conf using the text editor program listed under Applications/Accessories and when I try to save the file it tells me I don't have the necessary permissions.  How do I accomplish this?

---

### Post by Seisen on 2007-04-30
To do that go to the terminal and put this in 

```
gksudo gedit /etc/X11/xorg.conf
``` this will give you super user rights and the ability to write to the file and save it.

---

### Post by Josey on 2007-04-30
sudo & gksudo change the user to root giving you total control over your system.

Make sure you know what your doing though as editing files like xorg.conf can break your system so use with caution.

There's a reason these files need root access.  :)

---

### Post by Spike-X on 2007-04-30
ALWAYS, BEFORE EDITING XORG.CONF, YOU SHOULD BACK IT UP:


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

To restore the backup:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by kstella on 2007-05-03
> **Spike-X said:**
> ALWAYS, BEFORE EDITING XORG.CONF, YOU SHOULD BACK IT UP:


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

To restore the backup:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Does "restore the backup" mean that if xorg.conf fails, the backup file will load instead? And does that mean that from then on, xorg.conf_backup is your xorg file?

---

### Post by 5-HT on 2007-05-03
> **kstella said:**
> Does "restore the backup" mean that if xorg.conf fails, the backup file will load instead? And does that mean that from then on, xorg.conf_backup is your xorg file?

Unfortunately, if the X server cannot load you will need to manually restore the backup xorg.conf (xorg.conf will always be the xorg file). In such situations, you will be dropped to a shell and can restore the backup xorg.conf by issuing the following:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```To restart X:
```
sudo /etc/init.d/gdm restart
```

---

