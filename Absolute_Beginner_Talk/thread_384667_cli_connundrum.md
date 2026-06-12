---
title: "cli connundrum"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-14
Hi, Please patronise me;


I need to make a permanent change to the mount options in /etc/fstab. Is this an editor ? sudo /etc/fstab won't take me there?

---

### Post by bukwirm on 2007-03-14
/etc/fstab is a file.
Edit it with "sudo gedit /etc/fstab".
Try google for more information.

---

### Post by arochester on 2007-03-14
Try > sudo gedit /etc/fstab

---

### Post by aysiu on 2007-03-14
Or, more appropriately, ```
gksudo gedit /etc/fstab
```

*gksudo* for graphical applications. *sudo* for terminal applications.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If you're using Kubuntu ```
kdesu kate /etc/fstab
``` If you're using Xubuntu ```
gksudo mousepad /etc/fstab
```

---

