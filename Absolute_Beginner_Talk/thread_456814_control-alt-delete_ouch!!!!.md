---
title: "control-alt-delete ouch!!!!"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by racevskis on 2007-05-28
in windows when a program freezes (often) you can press control-alt-delete to manually end program.............is there a way to end programs in ubuntu in the same way ..................i had this problem while trying to install and it kept the .deb installer open even after a reboot...............the only way i could fix it was to reinstall ubuntu 3 times.............ouch!please could someone help i would be most grateful................

---

### Post by Ek0nomik on 2007-05-28
System/Administration/System Monitor

or type this into the terminal:

```
gnome-system-monitor
```

---

### Post by hellmet on 2007-05-28
If I'm not wrong, there is a s/w on Automatix, that fires up System-Monitor when you press Ctrl-Alt-Del.

---

### Post by ramjet_1953 on 2007-05-28
Right-click on a blank section of either the top, or bottom panels.

Select [COLOR="Blue"]Add to Panel[/COLOR]

When the window opens, choose [COLOR="Blue"]Force Quit [/COLOR]from the Desktop and Windows section.
 
When an application freezes just click on the Force Quit icon which you placed on the panel and then click on the window of the frozen application.

Regards,
Roger :cool:

---

### Post by racevskis on 2007-05-28
thanks guys .................. i had the same problem just after posting so yet another fresh install.................but no more with your tips in hand  ha ha ha

---

### Post by ryanVickers on 2007-05-28
That's all great advice.  Also, if it's a really bad problem, you can co Ctrl Alt Backspace and it kills the graphical system without hurting th OS (windows is unable to do this due to bad design).  It then goes to the login and you can continue, although you are likily to lose anyhting you had open, unless it was run from the terminal in a special way.

---

### Post by aysiu on 2007-05-28
Alt-F2 ```
xkill
```

---

### Post by loathsome on 2007-05-28
.. did you have to REINSTALL? You could just 'killall' it, though.

---

