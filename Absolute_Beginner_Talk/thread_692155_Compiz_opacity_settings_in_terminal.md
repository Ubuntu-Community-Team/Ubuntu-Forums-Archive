---
title: "Compiz opacity settings in terminal"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by cr0bar on 2008-02-09
So I kinda made a boo-boo earlier on today. I set the opacity too far the wrong way in Compiz and so now everything's invisible. What would the terminal command be to alter the opacity settings back to something more visible?

---

### Post by PinkFloyd102489 on 2008-02-09
If you have a scroll mouse, I think it's Ctrl+Alt+Scroll to change the opacity.


EDIT: It's Alt+Button4 and Alt+Button5, which is the scroll wheel.

---

### Post by cr0bar on 2008-02-10
Unfortunately that didn't aid me in restoring any window visibility or the top and bottom bars. If there's a command for altering the opacity settings in safe mode I believe that would be beneficial.

---

### Post by benerivo on 2008-02-10
The settings will be stored somewhere in files contained in these folders, but it's not obvious.

/home/ben/.gconf/apps/compiz
/home/ben/.config/compiz/

It may be easier to uninstall compiz-gnome, then log in. It should start with the metacity window manager. The advanced settings package should still be available, so you can change your settings. The reinstall compiz-gnome and restart.

```
sudo apt-get remove compiz-gnome
```

---

