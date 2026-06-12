---
title: "How would I go about uninstalling Compiz Fusion?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-07-25
If I were to follow [this guide]("http://ubuntuforums.org/showthread.php?t=481314") and install Compiz Fusion on my low end GPU machine, how would I go about uninstalling it later if my GPU slows down or if I don't like it?

Thanks for your help.

---

### Post by rich.bradshaw on 2007-07-25
Just change the

sudo apt-get install

to

sudo apt-get remove

at the beginning of the line where you installed it.

i.e. change

sudo apt-get **install **compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

to

sudo apt-get **remove** compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

---

### Post by dreadlord_chris on 2007-07-25
> **Majorix said:**
> If I were to follow [this guide]("http://ubuntuforums.org/showthread.php?t=481314") and install Compiz Fusion on my low end GPU machine, how would I go about uninstalling it later if my GPU slows down or if I don't like it?

Thanks for your help.

for GNOME Desktop:
```

sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

```
for KDE
```

sudo apt-get remove compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-kconfig

```

---

### Post by Majorix on 2007-07-25
Ok thanks. Do I need to edit any config files then? Or will everything be back to normal once I "remove" the packages?

---

### Post by Gadren on 2007-07-25
When at the login screen, you can choose your "session" from "GNOME with XGL" to just "GNOME."  That will have you load a desktop without Compiz.

---

### Post by Majorix on 2007-07-25
Oh thanks I didn't know about feature. Thanks for making me aware, might use it :)

---

### Post by dreadlord_chris on 2007-07-25
> **Gadren said:**
> When at the login screen, you can choose your "session" from "GNOME with XGL" to just "GNOME."  That will have you load a desktop without Compiz.

really? Because those session options are not just created with the default install of Compiz (at least not on mine) and should require some manual editing to create them.

---

### Post by Majorix on 2007-07-25
Yeah I also noticed that it is not the case with me. I have to manually start "compiz --replace" using Sessions Manager, so if I was to for example give up on compiz, I could just go and remove that entry.

---

### Post by dreadlord_chris on 2007-07-25
> **Majorix said:**
> Yeah I also noticed that it is not the case with me. I have to manually start "compiz --replace" using Sessions Manager, so if I was to for example give up on compiz, I could just go and remove that entry.

yup...

---

