---
title: "Gartoon icon theme thrash can"
date: 2007-02-10
forum: Art &amp; Design
---

### Post by Sabrage on 2007-02-10
HI. I installed the Gartoon icon-theme, and all the icons were installed automagically except the thrashcan.  I know it exists in the theme cause when I click properties on the home icon it is listed. I also tried deleting the trash can from the panel and installing it again but the same trash can appeared, not the gartoon one. Anyone know how I can install the gartoon trash can?

---

### Post by CarpKing on 2007-02-11
Maybe try
```
killall gnome-panel
```
after you install the theme?

---

### Post by Sabrage on 2007-02-11
Thanks CarpKing. I tried it but i still get the same...

---

### Post by ivoencarnacao on 2007-04-15
> **Sabrage said:**
> HI. I installed the Gartoon icon-theme, and all the icons were installed automagically except the thrashcan.  I know it exists in the theme cause when I click properties on the home icon it is listed. I also tried deleting the trash can from the panel and installing it again but the same trash can appeared, not the gartoon one. Anyone know how I can install the gartoon trash can?

I am having this problem too.

Does anyone know anyother way to fix this?

---

### Post by Sain on 2007-11-08
Another one here... nobody seems to know solution for this :-/

Too bad, gartoon icon theme is great, but that trashcan irks me! I believe it's somewhat ubuntu releated, cause i have seen it on debian and it works.

What about edubuntu? It has gartoon icons by default...

---

### Post by kikke on 2007-11-08
update-icon-caches after replace?

---

### Post by Sain on 2007-11-09
Does not work... but i noticed that I can have the correct trash icon od the desktop, if I enable it in configuration editor. 

Icon in nautilus and AWN still remains default one.

---

### Post by CarpKing on 2007-11-09
Sounds like it's missing a link within the package.  Unfortunately I'm not sure which links need to be there, but I know I've seen other threads that had the same problem with other icon sets.

---

### Post by ubuntu-freak on 2007-11-15
It's not a Ubuntu problem. Gartoon is 2 years old now and is not completely compatible with the latest Gnome. If you unpack the Gartoon theme and find the trash icon, copy it, then rename it 'user-trash.svg' and copy the trash full icon naming it 'user-trash-full.svg, then replace your current theme with that one you will get the trash icon in your panel again. There are many icons in Gartoon with outdated filenames. I suggest you download 'Dropdown Neu' and copy the filenames from that for Gartoon. That's what I used as a guide. Gartoon doesn't even have a shutdown icon. I copied the big red X and named it 'gnome-shutdown.svg. Looks pretty funky. It was either that or the default grey one in Debian. Bleh. Hope that helps.

---

