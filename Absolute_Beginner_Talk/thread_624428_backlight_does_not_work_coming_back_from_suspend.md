---
title: "backlight does not work coming back from suspend"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by legoman666 on 2007-11-26
hi,
I just installed Ubuntu on my Lenovo R61. this is basically my first time using linux so I really don't know what the hell im doing :D.

Anyway, everything seems to work great right off the bat except suspend. When I try to resume from suspend, the backlight does not turn back on. I can see the LCD dimly, but the light is off. Is there a way to fix this?

---

### Post by jordanmthomas on 2007-11-27
Please don't take my solution as a "Linux isn't friendly" thing, but here goes:
first try this:  press ctrl-alt-f1 and then ctrl-alt-f7
does this bring your light back?

if not, try adjusting the brightness using your keyboard to see if it turns the backlight on.

if not, here's the next thing you can try:
open a terminal:
```
gksudo gedit /usr/bin/on
```
paste this into the file:
```
#!/bin/bash
xset -display :0 dpms force on

```
save it and close gedit.
In your terminal, type ```
sudo chmod +x /usr/bin/on
```
Then, after the next time your system suspends, press Alt + F2 and type on and hit enter.
If this works, you can set a keyboard shortcut for it (that's what I do anyway)


Like I said, don't think these are the only ways to "fix" it (if you can call what I've given you a fix).  In fact, I am pretty certain there's a way to fix it by editing a file called lid.sh (not sure where it is or how to edit it though).

---

### Post by legoman666 on 2007-11-29
the ctrl-alt-f1 then ctrl-alt-f7 turns the back light back on. Using the function keys on my keyboard doesn't do anything until the light is back on. I'll give your other sugestions a shot when I get home. Thanks.

---

### Post by nick_h on 2007-11-29
> **legoman666 said:**
> the ctrl-alt-f1 then ctrl-alt-f7 turns the back light back on. 

You could try setting DOUBLE_CONSOLE_SWITCH=true in your /etc/default/acpi-support file.

---

### Post by tnt0 on 2008-01-13
> **nick_h said:**
> You could try setting DOUBLE_CONSOLE_SWITCH=true in your /etc/default/acpi-support file.

THX! It's work now.

---

