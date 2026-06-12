---
title: "install icon pack"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by stubblepoo on 2008-04-19
i have this black_white_2_Neon_by_DBGtheKafu.tar icon pack from gnome-look, i had it installed before than reinstalled ubuntu and cannot get it to install again, i can't remember how i did it the first time. any suggestions, i cannot move it into the /usr.../icons as i don't have the permissions. dragging it into the icon tab in theme manager doesn't do anything either.

---

### Post by joshrobinson on 2008-04-19
> **stubblepoo said:**
> i have this black_white_2_Neon_by_DBGtheKafu.tar icon pack from gnome-look, i had it installed before than reinstalled ubuntu and cannot get it to install again, i can't remember how i did it the first time. any suggestions, i cannot move it into the /usr.../icons as i don't have the permissions. dragging it into the icon tab in theme manager doesn't do anything either.

is there any special notes on gnome-look?
have you tried using the install button on the main "Theme" tab of appearance options?

---

### Post by nicedude on 2008-04-19
Should be as easy as going to top desktop toolbar then,
System -> Preferences -> Appearance

Then Just drag the Icon theme onto the appearance GUI and it will install automatically.

Though I noticed your package ends in just .tar all mine ( like 20 or so) end in .tar.gz
so you might want to make sure that doesn't matter as well.

---

### Post by joshrobinson on 2008-04-19
> **nicedude said:**
> Should be as easy as going to top desktop toolbar then,
System -> Preferences -> Appearance

Then Just drag the Icon theme onto the appearance GUI and it will install automatically.

Though I noticed your package ends in just .tar all mine ( like 20 or so) end in .tar.gz
so you might want to make sure that doesn't matter as well.

you just jogged my memory saying it ended in .tar only
extract the tar file, there should be a .tar.gz inside the .tar

i think i tried that icon pack before

---

### Post by sayakb on 2008-04-19
Open a terminal and type:
```
gksudo nautilus
```Now extract and copy it to /usr/share/icons through the root Nautilus window (But be careful with it)

---

### Post by fallenshadow on 2008-04-19
> extract the tar file, there should be a .tar.gz inside the .tar

This is correct... extract the tar and you should find another zipped folder inside. Drag and drop this over appearance window not icons tab and click customize on the theme you want the icons for.

---

