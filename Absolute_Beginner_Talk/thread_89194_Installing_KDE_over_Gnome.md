---
title: "Installing KDE over Gnome"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by generalstoner on 2005-11-12
I am using Ubuntu with gnome and would like to know how to install KDE over Gnome without using kubuntu...I would install kubuntu but all the burner programs lockup when formatting a dvd-rw So i would appreciate either directions to install KDE and remove Gnome or a solution to my burner programs. Thanks in advance

---

### Post by aysiu on 2005-11-12
You don't have to use KDE burner programs just because they're installed. You can still use Nautilus, Gnomebaker, or Graveman. That said, you also don't have to install the *kubuntu-desktop* meta-package. You can just install KDE ```
sudo apt-get update
sudo apt-get install kde
```

---

### Post by generalstoner on 2005-11-12
I have KDE installed now but I cant use the toolbar or anything else like that. I cant get the prefrences or anything, that is what I was really after. any ideas, I would like to remove gnome if possible.

---

### Post by Kvark on 2005-11-12
Install kubuntu-desktop with synaptic or apt-get, then you will have a complete Kubuntu system with all the KDE apps.
```
sudo apt-get install kubuntu-desktop
```

---

### Post by generalstoner on 2005-11-12
thanks a lot im in the middle of installing it right now, Hope it works out right, My computer has a nasty habit messin up on me...

---

### Post by sanguinemoon on 2005-11-14
Will doing that destroy the Gnome Desktop? I like to see a complete KDE desktop for testing purposes, but I'd still like to be able boot into Gnome

---

### Post by aysiu on 2005-11-14
[QUOTE=sanguinemoon]Will doing that destroy the Gnome Desktop? I like to see a complete KDE desktop for testing purposes, but I'd still like to be able boot into Gnome[/QUOTE] No. Gnome will still be there. At login, you'll have the choice to boot into Gnome or KDE. I should warn you, though, that installing Kubuntu-desktop will clutter up your Gnome menus with a whole bunch of KDE programs.

---

### Post by Adrian on 2005-11-15
> I should warn you, though, that installing Kubuntu-desktop will clutter up your Gnome menus with a whole bunch of KDE programs.

It is however possible to prevent Kubuntu programs from showing up in Gnome.
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

---

### Post by sanguinemoon on 2005-11-15
Ok, I installed the Kubuntu package, but I liked Gnome better :lol:

---

