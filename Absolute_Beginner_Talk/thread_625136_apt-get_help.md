---
title: "apt-get help"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Jammer429 on 2007-11-27
I have had ubuntu before but I can't remember how to use apt-get I can't figure out what the deal is..is there something I have to download first.I open my download and type apt-get install wine or amarok and it says no package  available  I have downloaded them before but I had ubuntu 704 now I have 710 please help me I am so lost

---

### Post by Belyel on 2007-11-27
My guess is that you need to activate your other software repositories, such as the universe and multiverse.  To do so, go to System>Administration>Software Sources.  Then make sure all the check boxes are selected for (main, universe, restricted, multiverse).

When using apt-get make sure you are using ```
sudo apt-get install
```

---

### Post by Jammer429 on 2007-11-27
That done it thanks alot I didn't have to do that last time now I just have to firgure out how to get beryl working

---

### Post by PeterJS on 2007-11-27
> **Jammer429 said:**
> That done it thanks alot I didn't have to do that last time now I just have to firgure out how to get beryl working

There is no more beryl; beryl and compiz have been merged and the new project is called compiz fusion. And the packages you want are compiz, compizconfig-settings-manager, and optionally gnome-compiz-settings and compiz-fusion-plugins-extras.

---

