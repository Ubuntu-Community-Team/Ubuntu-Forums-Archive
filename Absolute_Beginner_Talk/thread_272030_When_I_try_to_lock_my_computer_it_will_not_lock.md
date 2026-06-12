---
title: "When I try to lock my computer it will not lock"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Darrious on 2006-10-05
When I click on the quit button in ubuntu. I click Lock Screen. This does not seem to work though. It did at first and now it just stopped. I mean that I click on it and nothing happens. I need this feature implemented in ubuntu.

---

### Post by petri on 2006-10-05
Happens to me sometimes too when I play with my xorg.conf. Do you have an ATI? Install the drivers [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Restart also helps and maybe ```
sudo killall gnome-panel
``` which restarts your panels.

---

### Post by transactionlogfiller on 2006-10-05
I think this can happen if the screensaver demon is not running.

Try "xscreensaver --no-splash &" from a terminal.

---

### Post by Darrious on 2006-10-05
The screensaver does work so I know that command would not do. I tried ```
killall gnome-panel
```

That Worked.

---

