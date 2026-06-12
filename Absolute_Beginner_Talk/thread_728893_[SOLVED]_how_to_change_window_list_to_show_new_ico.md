---
title: "[SOLVED] how to change window list to show new icon"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by DarinB on 2008-03-19
i changed my rhythmbox icon i want it to come up in the window list as the new icon.
i found the con in /usr/share/icons/hicolor/scalable/apps that is called Rythmbox.svg
i think if i change that one it will work. will it??????????????????
i don't have privileges to add the new icon i did copy it and rename it to rythmbox.svg
but it won't let me replace the one that is there
help on this???????????????????????????????????????????????????????????????????????

---

### Post by philinux on 2008-03-19
You need to use this from the terminal.

```
gksudo nautilus
```

This gives you a root privilege file browser so be careful.

---

### Post by DarinB on 2008-03-19
well copying over the icons i found didn't work
when i open rythmbox the icon in the window list comes up briefly then reverts to the old one.
any ideas maybe i have to copy the icon i use to somewhere else??
i thought it was hicolor maybe not 
any ideas?????????????????????

---

### Post by DarinB on 2008-03-19
i solved it...
logged in as root gksudo nautillus
then navigated to usr/share/icon/<mytheme>/16x16/
i replaced the .png with what i did take the desktop icon and resized it and converted it from a .svg to a .png in gimp.
now the wondow icon list shows the same icon i changed the desktop icon to.
what a pain but it worked.

---

