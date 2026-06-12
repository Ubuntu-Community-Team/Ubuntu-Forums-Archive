---
title: "Desktop Icons"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-02-01
I've just installed Edgy (linux-generic) on our second computer and I just can't get the Home Folder and Computer Desktop icons to appear (as they did immediately when I installed Edgy (linux-386) on the other computer.

What's the secret?

---

### Post by ComplexNumber on 2007-02-01
> **PaulFXH said:**
> I've just installed Edgy (linux-generic) on our second computer and I just can't get the Home Folder and Computer Desktop icons to appear (as they did immediately when I installed Edgy (linux-386) on the other computer.

What's the secret?
for the time being, fire up the terminal and enter 'gconf-editor'. in gconf-editor, do a search for "nautilus".  the 2nd hit that it gives should be apps/desktop/nautilus. you can tick the tickboxes there so that those icons appear.


btw if you cant see a program called Configuration Editor(ie gconf-editor) in system tools in your menu, then go to your menu button, right click on it, then press 'edit menus' have a look for configuration editor in system tools and see if its visible. i think when i first installed ubuntu, it wasn't visible. make it visible because its a really useful application.

---

### Post by PaulFXH on 2007-02-01
Hi ComplexNumber
Thanks for the explanation.
Actually, I wasn't even aware that *system tools* could be part of the Apps menu.
My new desktop is now as it should be.
Best wishes
Paul

---

