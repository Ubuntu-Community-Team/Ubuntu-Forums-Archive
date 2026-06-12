---
title: "Splash screen"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-06-18
When I log in from the graphical login screen, the system displays a brown background while showing the gnome splash screen. Is it possible to change the color of this background? If so, how?

---

### Post by Xian on 2005-06-18
[QUOTE=Zaare]When I log in from the graphical login screen, the system displays a brown background while showing the gnome splash screen. Is it possible to change the color of this background? If so, how?[/QUOTE]
You just need to open the gdm setup module.
To do this open a terminal and use the command below.
Then click on the 'Standard Greeter' tab.

Look at the bottom right-hand corner.
See the box that says 'Background Color'?

Change that to match what you prefer.
Logout/Login

```
$ sudo gdmsetup
```

---

### Post by Zaare on 2005-06-18
Ah, thanks. I had only looked in the graphical greeter.

---

