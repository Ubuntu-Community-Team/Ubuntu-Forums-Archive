---
title: "[SOLVED] Removing KDE apps"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-09-17
I recently removed ktorrent and k3b from my Gnome desktop.  

How can i make sure all of the additional libraries and config files have been purged?

I uninstalled both apps with synaptic packet manager.

Thanks!

---

### Post by alienexplorers on 2007-09-17
Try this:
> [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

### Post by lmlypfan on 2007-09-17
I never installed the full KDE desktop, just a couple of KDE apps.

If i try sudo aptitude remove kde-desktop:

nothing is removed.

Again, I just installed some KDE apps, and want to make sure all libraries, config files, and such are completely gone.

Thanks

---

### Post by alienexplorers on 2007-09-17
Try sudo aptitude remove  /directory/filename.

---

### Post by Maestro23 on 2007-09-17
> sudo aptitude purge pkgname

Deletes config files as well.

---

### Post by lmlypfan on 2007-09-17
Thanks maestro

---

