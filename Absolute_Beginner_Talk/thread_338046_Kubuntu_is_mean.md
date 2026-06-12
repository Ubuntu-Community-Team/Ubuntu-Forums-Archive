---
title: "Kubuntu is mean"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-13
i installed kubuntu, but now I can't make GDM manage the login window. Also, how do I make the boot screen have the ubuntu logo, and not the kubuntu one?

I think it's possible by deleting all Kubuntu files that were installed when setting up kubuntu-desktop. Where can I find these? Like, the desktop files?

---

### Post by sean_ on 2007-01-13
> **kbsuperstar said:**
> i installed kubuntu, but now I can't make GDM manage the login window. Also, how do I make the boot screen have the ubuntu logo, and not the kubuntu one?

I think it's possible by deleting all Kubuntu files that were installed when setting up kubuntu-desktop. Where can I find these? Like, the desktop files? What?

---

### Post by ComplexNumber on 2007-01-13
> **kbsuperstar said:**
> i installed kubuntu, but now I can't make GDM manage the login window. Also, how do I make the boot screen have the ubuntu logo, and not the kubuntu one?

I think it's possible by deleting all Kubuntu files that were installed when setting up kubuntu-desktop. Where can I find these? Like, the desktop files?
is gnome installed or have you now uninstalled it?

---

### Post by kbsuperstar on 2007-01-13
it's still installed

---

### Post by %hMa@?b&lt;C on 2007-01-13
sudo dpkg-reconfigure gdm
huzzah!

---

### Post by kbsuperstar on 2007-01-13
that file doesn't exist

---

### Post by ComplexNumber on 2007-01-13
**kbsuperstar**
are you wanting to keep GDM(rather than KDM) as your login manager even though you are using kubuntu? if so,  go to the terminal and type in 'gksudo gdmsetup'.

---

### Post by kbsuperstar on 2007-01-13
I'm using Gnome desktop, but KDM is the login window now. I don't know how to enable GDM and to change the boot logo back to the normal ubuntu one

---

### Post by ComplexNumber on 2007-01-13
there might be some automated way to change it, but i'm not aware of it. however, you can go to this file: /etc/X11/default-display-manager. in your situation, it should say the path to kdm. change it to /usr/sbin/gdm

---

### Post by %hMa@?b&lt;C on 2007-01-13
sudo dpkg-reconfigure gdm 
should work if you havent removed gdm 
you may need to aptitude install gdm then.

---

