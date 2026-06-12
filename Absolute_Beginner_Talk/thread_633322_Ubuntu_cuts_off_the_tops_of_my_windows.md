---
title: "Ubuntu cuts off the tops of my windows"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Hitane on 2007-12-06
[IMG]http://i24.photobucket.com/albums/c11/DeadpoolX23/Screenshot.png[/IMG]

If you look closely, you'll see that my windows have had the tops chopped off (the bit above the main toolbar, meaning I can't really minimize or anything), and I *think* the problem is related to the "extra" visual effects, the ones that make Linux act like a mac, but I turned them off and the problem still isn't fixed...

---

### Post by philinux on 2007-12-06
Try system>pref>appearance then customise the theme you running and then select the tab windows borders. See if changing anything in there works.

---

### Post by pointone on 2007-12-06
Alt+F2

```
gtk-window-decorator --replace
```

---

### Post by blu3ness on 2007-12-06
means that your windows decorator is not running, and also, Alt +F2 doesn't work when y ou don't have a windows decorator,

try to open up a terminal, then type 
gtk-window-decorator --replace

or 

emerald --replace

If you get error messages, post them :P

this is a very common symptom from trying to install compiz.

---

### Post by Hitane on 2007-12-06
The GTK code worked! Also, I'm installing Emerald, I didn't have it before, so just in case...

Thanks everyone!

---

### Post by Hitane on 2007-12-06
Ok, now a new problem :(

Whenever I close terminal the tops disappear again. I open terminal and restore them, but without terminal they go. Neither codes (emerald or GTK) is permanently keeping the windows

---

### Post by Hospadar on 2007-12-06
well when you restart, I think the window decorations should come back.  also you could try prepending "nohup" to the decorator command, for example "nohup emerald --replace"  nohup prevents a process for exiting when its shell exits.

---

### Post by Krydahl on 2007-12-06
A simple fix that sometimes works:

Go into System -> Preferences -> Advanced Desktop Effects

(If you don't have this, you need to install compizconfig-settings-manager.)

Make sure that Windows Decorator is active (tick the box next to it). Go into there and in the command box type the name of the decorator you want to use (either Emerald or gtk-window-decorator (Emerald if you want fancy window decorations).

---

### Post by Hitane on 2007-12-06
I tried a restart and it's fixed now, but if it messes up again, at least I can find this thread again

Thanks :)

---

