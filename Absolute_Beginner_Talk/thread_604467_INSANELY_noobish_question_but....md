---
title: "INSANELY noobish question but..."
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Xeeon on 2007-11-06
How would I go about elevating myself as root?

I'm trying to edit my xorg.conf file and I apparently have to be root to do anything to it..

```

*Could not save the file /etc/X11/xorg.conf.*

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```

^^^That is the error I got..

---

### Post by mike^_^ on 2007-11-06
```
sudo nano -w /etc/X11/xorg.conf
```

or if you prefer a graphical editor 

```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by laidback on 2007-11-06
You need to use sudo:-

$sudo gedt filename

$password (your usual password)

You'll then be put into Gedit with the filename of your choice. Filename can include  a path, in most cases I find it will. e.g sudo gedit /etc/fstab

The sudo command allows you to perform the next command as root ( sudo gedit)
Use with care.
If you have put in your password recently (last 10 mins) it wont ask you for it.

---

### Post by Xeeon on 2007-11-06
Thank you very much! I will remember that from now on.

---

### Post by sneezymelon on 2007-11-06
simply type "sudo" before your command

---

