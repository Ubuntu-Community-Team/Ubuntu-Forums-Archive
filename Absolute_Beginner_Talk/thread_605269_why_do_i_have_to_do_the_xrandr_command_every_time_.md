---
title: "why do i have to do the xrandr command every time i log on to ubuntu?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-11-06
I have to do 
> xrandr --output DVI-1 --left-of DVI-0 everytime I log back on to Ubuntu (after a reboot or shutdown) if I want to enjoy dual-monitor setup.
Why do i have to do the xrandr command every time i log on to ubuntu?


If I don't do that command. I have just a single monitor setup. Is there a way for Ubuntu to automatically do that command every time?

---

### Post by MaximusTG on 2007-11-08
You could edit your xorg.conf to do that. But I couldn't tell you how to put your config into xorg.conf. As a quick fix, you could add that xrandr line to your session's startup program. Then ubuntu will automatically execute it every time you login.

---

