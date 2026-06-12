---
title: "hotkey"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by xieu90 on 2008-04-20
yesterday I bought a new keyboard
and there is a button looks like moon, I think it is sleep for windows
and where I press it my computer will be turned off
when I press power button it will show ic mac ........ and then I hear my music which was running and it freezes and I have to restart again
in system-preferences-keyboard shortcut I didn't find anything related to that button, I want to change it to something else, since it is very near to ESC and it might kill me anytime
I changed it to eject in keyboard shortcut, but when I press it my computer is dead, 
what should I do now ?

---

### Post by felicity on 2008-04-20
You can start gconf-editor:

```
gconf-editor
```

then navigate in gconf-editor to apps, gnome-power-manager, buttons. Change the Value entry for the "power" Name. The Value entry should say interactive right now. Change the word interactive to the word nothing.

That should fix it!

---

### Post by xieu90 on 2008-04-20
thank you it worked :lolflag:

---

