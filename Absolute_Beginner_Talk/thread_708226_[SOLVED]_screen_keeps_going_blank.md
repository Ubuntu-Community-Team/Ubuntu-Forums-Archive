---
title: "[SOLVED] screen keeps going blank"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by noremacyug on 2008-02-26
ok, after about 10 mins my screen will go black and when i hit the mouse or what not, it comes back on.  now i know what you're thinking, " it's a screen saver ya idiot" or perhaps "check your power settings ya moron."  thing is, i have, both of them.  that was the first thing i headed to and disabled and it still does it.  what am i missing fellas?

here's a screenie of my screensaver and power managment settings.

---

### Post by oedha on 2008-02-26
since you choose blank screen as screen saver...you'll get blank screen
what if you change the picture ?

---

### Post by noremacyug on 2008-02-26
i had it set to blank screen for the screen shot, but it was previously set to random and i still always got a blank screen.  plus, as you can see, i don't have the "activate the screensaver when the computer is idle" box checked.

---

### Post by jw5801 on 2008-02-26
This is due to X being annoying. You can try adding the following to /etc/X11/xorg.conf
```

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

```

Then log out and back in again and it shouldn't happen anymore. Of course it means the screen won't turn off at all without manual input, which can also be irritating.

---

### Post by noremacyug on 2008-02-26
thanks, i'll have to give that a try

---

### Post by noremacyug on 2008-03-07
that fixed the issue.  thanks!

---

