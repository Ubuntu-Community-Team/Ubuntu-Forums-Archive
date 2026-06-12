---
title: "Emerald Crashing"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Valon Majere on 2008-02-04
I'm not exactly new to Ubuntu but this is my first time using it seriously. I'm using Ubuntu 7.10 and am having trouble with Emerald theme manager crashing. I use emerald --replace to start it but as soon as i close the terminal, emerald crashes. i have tried emerald --replace & as well as sudo emerald --replace & as they were recommended on a similar post but neither have worked. In the end i used metacity --replace, but i would prefer to use emerald. Any help is greatly appreciated.

---

### Post by spiderbatdad on 2008-02-04
I believe ccsm will automatically use emerald as long as you have installed it and selected a theme under System>>Preferences>>Emerald. Hope this helps. Also you can run a program with alt-F2 if you want it to fork, so that it still runs after the terminal is closed.

---

### Post by kpkeerthi on 2008-02-04
Emerald crashes randomly for me too. While I'm still hoping for a fix sometime in the future, I'm using [gtk-window-decorator]("http://wiki.opencompositing.org/Decorators/GTKWindowDecorator") to apply metacity window decorations to compiz-enabled desktop. Run this command after compiz starts up.
```
gtk-window-decorator --replace
```

Alternatively, if you have compiz config settings manager (ccsm) installed, you can add this command under
ccsm->Window Decoration->Command
.. and restart compiz.

---

### Post by Valon Majere on 2008-02-04
i had no problems with compiz working in concert with metacity but now that ive installed emerald and tried to use it with compiz my window borders dissappear and now that i used metacity --replace i have everything back except i cannot run compiz without it trying to start emerald which then crashes. I tried gtk-window-decorator --replace but nothing happened at all, also i have tried running emerald with alt + F2 still gives me the problem of emerald crashing after the terminal closes, btw i don't have a theme selected under emerald but it did apply one when i first started it and it stayed there for a few seconds then crashed.

---

### Post by Valon Majere on 2008-02-05
i now believe ive got Compiz using the gtk - window-decorator, i was able to find a command on another post that let me purge emerald(sudo apt-get remove --purge emerald) and apparently it defaulted to gtk,(i also put that code in under ccsm kpkeerthi  so that may be what finally did it) but now im getting an error with Compiz (/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop). This error shows up right after gtk -window-decorator starts up in terminal. I would still like to use emerald but with the bug i would be happy to just get compiz working again with gtk. While i do have compiz using gtk by default now i still dont have any window borders when i use compiz.

---

