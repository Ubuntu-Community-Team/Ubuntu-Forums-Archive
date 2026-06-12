---
title: "[SOLVED] Desk Top Icons"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by ibbill on 2007-12-29
Hi have rebooted up 3 times still no luck all the icons are missing from the desktop

They are still listed under Places/ Desktop but not showing on my desk top.:confused:

I tried to drag them from the desktop folder with no luck

---

### Post by SOULRiDER on 2007-12-29
I used to have a problem like this when i created a new folder and it didnt appear, i had to drag it to the desktop. If that doesnt work, is it possible that you changed your configuration so that you dont see any icons?

---

### Post by ibbill on 2007-12-29
Thanks for the reply. Had turned the monitor off for the night as usual and then when I would turn it back on in the morning the desktop would be fine.

This morning when I turned it on poof no desktop icons. In fact when I try and drag anything to the desktop it will not stay. Also if I right click on the desk top nothing shows at all.

---

### Post by SOULRiDER on 2007-12-29
Restart Xorg, press **ctrl + alt + backspace**

---

### Post by ibbill on 2007-12-29
tried the following and this is what showed up on the restart. Screen shot would not go to my desktop but in my desktop folder under places/desktop

---

### Post by jryprt on 2007-12-29
In a terminal type:

    gconf-editor

Browse to apps > nautilus > preferences > show_desktop and see if it is checked if not select it .

---

### Post by ibbill on 2007-12-29
this is what I have sorry for all the trouble here.

---

### Post by ibbill on 2007-12-29
Have no idea what happen rebooted again with the ctrl alt backspace and the desktop is back.

Thank you both ever so much

---

### Post by SOULRiDER on 2007-12-29
Nautilus probably crashed thats why your desktop wasnt showing properly.

---

