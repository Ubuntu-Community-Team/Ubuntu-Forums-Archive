---
title: "menu editor eat up my menu ...!!!"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-06-29
I installed my Xubuntu, and when tried the xcfe4-menu editor it ate up my menu and i can not access anything now, no terminal access, no application access ....

At the Fix release it says " remove ~/.config/xfce4/desktop/menu.xml, log out from Xfce and then log in again. "

But it did not say how to remove, where to find such path .....:confused: :confused: :confused: 

Any help please, thanks .....

---

### Post by angkor on 2006-06-29
[QUOTE=mourad]I installed my Xubuntu, and when tried the xcfe4-menu editor it ate up my menu and i can not access anything now, no terminal access, no application access ....

At the Fix release it says " remove ~/.config/xfce4/desktop/menu.xml, log out from Xfce and then log in again. "

But it did not say how to remove, where to find such path .....:confused: :confused: :confused: 

Any help please, thanks .....[/QUOTE]

Type Ctrl+Alt+F1

This will take you to the console. After you log in you can delete (or move the file if you're unsure).

```
rm .config/xfce4/desktop/menu.xml
```

or if you want to move it

```
mv .config/xfce4/desktop/menu.xml .config/xfce4/desktop/menu.xml_backup
```

After that you can return to xfce4 with Ctrl+Alt+F7.

Maybe you need to relogin. Type Ctrl+Alt+Backspace to kill X and it takes you back to the login screen. Hope this helps.

---

