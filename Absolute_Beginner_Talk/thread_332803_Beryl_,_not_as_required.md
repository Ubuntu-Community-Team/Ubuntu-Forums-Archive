---
title: "Beryl , not as required"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by housam on 2007-01-06
Could anyone help me in this ?? . After installing Beryl , most windows opened in a slow motion and sometimes freeze. even mouse scrole is moving up and down in slow motion.and also I have an  automatic restart of my Laptop in a time intervals varies between 30 to 60 min.
I have a 950GMA Intel card and I already installed the newest version of xserver-xgl.
How could I solve this problem ?](*,)

---

### Post by Sasa_Ivanovic on 2007-01-06
you should solve it by uninstalling the beryl :
```

sudo apt-get remove --purge beryl emerald-themes

```
and restore your xorg.conf ( if you made a backup )

So to test that everything is fine after uninstalling it the output of the following :
```

glxinfo | grep direct

```
should be : direct drawing : yes

---

### Post by aidanr on 2007-01-06
theres a slow motion animation for effects, make sure thats not on, the keybinding is shift+f10 by default :-k

---

### Post by housam on 2007-01-06
I didn't make a backup before installing Beryl. how can I edit the " xorg.conf " file?
Also , is beryl not suitable for this card or what? If I installed it again ,I w'll face the same problems?

---

### Post by housam on 2007-01-06
> **aidanr said:**
> theres a slow motion animation for effects, make sure thats not on, the keybinding is shift+f10 by default :-k
N0. I have this slow motion even after switching to Gnome display manager.

---

### Post by Sasa_Ivanovic on 2007-01-06
you don't have to have backup, just remove beryl and reinstall your video drivers. If it doesn't work then you can generate "xorg.config" flie.

---

