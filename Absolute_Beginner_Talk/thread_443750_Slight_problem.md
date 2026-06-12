---
title: "Slight problem"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Anders J on 2007-05-14
Tried changing display options in xcorr.conf and happened to leave one of the display formats misspelled.

Now X refuses to start and I can only get into TTY mode.

Have backup of xcorr.conf, all I need to do now is to:
- login
- get myself sudo rights
- list the available files in /etc/X11 
- rename the appropiate one and
- reboot

and I should be up and running again.

List of ciommands anyone please!

---

### Post by taurus on 2007-05-14
```
cd /etc/X11
ls -la
sudo cp **xorg.conf.backup** xorg.conf
sudo /etc/init.d/gdm start
```
(assuming /etc/X11/xorg.conf.backup is the original version.)

---

### Post by annda on 2007-05-14
> **Anders J said:**
> Tried changing display options in xcorr.conf and happened to leave one of the display formats misspelled.

Now X refuses to start and I can only get into TTY mode.

Have backup of xcorr.conf, all I need to do now is to:
- login
- get myself sudo rights
- list the available files in /etc/X11 
- rename the appropiate one and
- reboot

and I should be up and running again.

List of ciommands anyone please!

just log in.

```
cd /etc/X11
```

to go to the directory.

list all the files:

```
ls -a
```

find the name of your backup.

```
sudo cp your_backup_filename xorg.conf
```

```
sudo reboot
```

i hope it is enough.

---

### Post by Anders J on 2007-05-14
Bless You! Worked! Thanks!

---

