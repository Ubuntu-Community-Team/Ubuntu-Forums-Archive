---
title: "This might be a Stupid Question"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Jason_howard on 2007-10-17
I have both Kde and Gnome on my lap top if I remove Kde will I be able to use kde programs Like k3b ect  and is this the way to remove it  sudo apt-get autoremove kubuntu-desktop

---

### Post by reckless2k2 on 2007-10-17
yes and yes. you can just do remove kubuntu-desktop though. even if it removes k3b, you can reinstall it without putting kde back on. 
enjoy

---

### Post by ticopelp on 2007-10-17
Kubuntu-desktop is a virtual package; removing it won't really do much. You can remove individual KDE applications and not hurt anything, and you can run KDE applications from GNOME without a problem. I use a lot of KDE apps daily under GNOME. You just have to install a few libraries with it, probably -- no big deal.

---

### Post by RomeReactor on 2007-10-17
Hi. As far as I know, that method will only remove the "kubuntu-desktop" metapackage, which is an empty package that serves to call the rest of the KDE programs for installation, so you'll still have to remove undesired KDE programs manually. So I think you'll still have the KDE desktop installed after that. How many KDE programs do plan on leaving installed? Is there a particular reason you want to remove the KDE desktop?

---

### Post by offroad64 on 2007-10-17
No such thing as a stupid question. Only stupid answers
K3B works just fine in Gnome and most other things will also

Jeff

---

### Post by maybeway36 on 2007-10-17
If you want to get rid of Kubuntu don't forget to do a
```
sudo apt-get autoremove
```

---

### Post by rjmdomingo2003 on 2007-10-17
[FONT="Trebuchet MS"][/FONT]Even when I'm in another window manager (i.e. fluxbox), I still can run K3B without a hitch. K3B :guitar:!!

---

