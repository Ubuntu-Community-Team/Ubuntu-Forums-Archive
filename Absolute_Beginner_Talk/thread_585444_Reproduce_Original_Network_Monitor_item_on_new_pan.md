---
title: "Reproduce Original Network Monitor item on new panel"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-10-21
How come the network monitor and power monitor that are by default in the top right of the screen can't be recreated.  I can add them to a new panel with the "add to panel" option but they are slightly different.

I'd like to create a new panel that also has the power and network items that behave like the defaults.

---

### Post by aktiwers on 2007-10-21
Im not sure what you are talking about?
Can you show a screenshot?

Is it any of the things on my screenshot?

---

### Post by Meson on 2007-10-21
Yeah, the pointer in the top left is correct.  The Power and Network items are not the same as the power and network items listed in the "Add to Panel" window.

---

### Post by aktiwers on 2007-10-21
If you right-click on that and hit properties, you can add Network, memory and so on.. and customize it. 

But if I understand correct, you want to have your Power(battery) shown the same way?

---

### Post by Meson on 2007-10-21
When I right click the original network item, it says enable networking, enable wireless, etc.  When I right click the one that I manually added to the panel, it gives the standard item menus with preferences, move, remove from panel, etc.

Similarly, the left click options are different.  I have a list of networks for the original icon, and the manually added one opens up a window with the connection properties for my ethernet devices.

---

### Post by aktiwers on 2007-10-21
> **Meson said:**
> When I right click the original network item, it says enable networking, enable wireless, etc.  When I right click the one that I manually added to the panel, it gives the standard item menus with preferences, move, remove from panel, etc.

Similarly, the left click options are different.  I have a list of networks for the original icon, and the manually added one opens up a window with the connection properties for my ethernet devices.

Ahh okay now I get it. Its because thats an app that is running in tray. If you look under System => Preferences => Session, you can see that Network Manager is in the startup list. So its running like a tray app.

Do you want to have more than one of those?
If you just want to move it around, I guess you have to move your whole tray around.

---

