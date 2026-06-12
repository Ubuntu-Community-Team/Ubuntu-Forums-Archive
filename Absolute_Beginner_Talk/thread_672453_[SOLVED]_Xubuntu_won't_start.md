---
title: "[SOLVED] Xubuntu won't start"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by marmaladeskies on 2008-01-19
Basically I've been using Xubuntu without problems for a couple months, and I decided to just go ahead and delete all the old Gnome applications.  So I did "sudo apt-get remove gnome*" and everything went fine and the internet, etc all still worked.  I turned off my computer, and when I tried to turn it back on, I see grub but that's it.  Recovery mode works.  How do I get to my Xubuntu GUI now? (And why would removing gnome apps stop Xubuntu from starting?)  Thanks!

---

### Post by Hallvor on 2008-01-19
You didn`t accidentally uninstall xubuntu-desktop, did you?

---

### Post by danillo on 2008-01-19
> **marmaladeskies said:**
> Basically I've been using Xubuntu without problems for a couple months, and I decided to just go ahead and delete all the old Gnome applications.  So I did "sudo apt-get remove gnome*" and everything went fine and the internet, etc all still worked.  I turned off my computer, and when I tried to turn it back on, I see grub but that's it.  Recovery mode works.  How do I get to my Xubuntu GUI now? (And why would removing gnome apps stop Xubuntu from starting?)  Thanks!

Uhm, for example it uses GDM, and gnome-mount i think... and it probably has some other gnome dependencies.

---

### Post by ryanVickers on 2008-01-19
yeah, it uses some stuff thats under gnome - I wold re-install xubuntu-desktop and see if it helps... it will add a few gnome things but only what it needs ;)

---

### Post by danillo on 2008-01-19
> **Hallvor said:**
> You didn`t accidentally uninstall xubuntu-desktop, did you?

I doubt that would wreck the system, since it's just a meta package.

---

### Post by Majorix on 2008-01-19
Danillo pretty much summed it up.

You can't remove all packages that start with "gnome". Also what about those that *end* with "gnome". You can't do it via a single-liner.

All I can suggest at the time being is recovering your home folder via the recovery mode and then reformatting the pc.

---

### Post by gn2 on 2008-01-19
In recovery mode type 
```
sudo apt-get install xubuntu-desktop
```
and it should re-install the GUI and all the required bits and pieces.

---

### Post by Majorix on 2008-01-19
Hmm haha why didn't I think of that :D

---

