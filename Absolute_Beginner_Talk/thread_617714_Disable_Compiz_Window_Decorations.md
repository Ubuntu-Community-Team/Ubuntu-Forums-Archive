---
title: "Disable Compiz Window Decorations"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by bmscwright on 2007-11-19
Im using compiz to do my effects, and i have the window decorations enabled. It gives me a  clear blue-ish bar on the top of my windows ([http://i8.tinypic.com/6xi0bvr.png](http://i8.tinypic.com/6xi0bvr.png)) and wont let me use the top bar that comes with my theme. When I disable the decorations in the compiz config. it gives me no top bar at all ([http://i4.tinypic.com/7xaaer6.png](http://i4.tinypic.com/7xaaer6.png)). Please help. Im new at this, but i can understand quite a bit.

---

### Post by stido on 2007-11-19
maybe [this thread]("http://ubuntuforums.org/showthread.php?t=486432") would help.
the disappearing titlebar has to do with the fact that no other window manager is running after you disabled compiz's window decorator.

---

### Post by DutyDuty on 2007-11-19
```
emerald --replace
then
compiz --replace &
```

---

### Post by bmscwright on 2007-11-19
I ran that code,
and now it went from having a red bar at the top of screens
to no bar whatsoever.
please help, im jammed.

---

### Post by jordanmthomas on 2007-11-19
instead of compiz --replace & do this
```
gtk-window-decorator &
```

---

### Post by dhobbs on 2007-11-19
If you're trying to use an emerald them you need to first have compiz enabled.  Then do the Alt+F2 and type in ```
emerald --replace &
```
If you want emerald to always run as your window manager you can go into the Compiz Config Settings Manager (Advanced Desktop Effects Settings) under System >> Preferences and click on the Effects tab and click on the Window Decorator button.  In the text box labeled "Command" you can type in ```
emerald --replace &
``` hit enter/return and it should always run when compiz is loaded.

(This is all assuming you want to use emerald and that you have emerald installed.)

---

### Post by bmscwright on 2007-11-19
I used the code gtk-window-decorator --replace    
IT WORKS PERFECTLY BUT
whenever i close the terminal window, it goes back to having no top bar on windows.
please help

---

### Post by jordanmthomas on 2007-11-19
Here's how I would remedy this problem (with gtk-window-decorator closing with the terminal)

type in ```
gtk-window-decorator --replace &
``` in your terminal.
Instead of clicking the close button to close the terminal, quit it either by typing
```
exit
```
or pressing Ctrl-d in the terminal.

---

