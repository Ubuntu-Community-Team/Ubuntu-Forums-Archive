---
title: "Problem logging into Gnome desktop"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by silv3r189 on 2008-01-15
Hi All,

I'm trying to figure out why I keep getting booted back in to the login screen after I enter my username/password.  The only way I'm able to log into Gnome is selecting "Failsafe GNOME session".  Does anyone have any ideas why I'm having trouble logging in?  The only thing I changed was my monitor type using the drop down menu in GNOME (System -> Administration -> Screens and Graphics).

Any ideas?  I'm an absolute Linux n00b and I have no idea how to fix this.

---

### Post by Blutack on 2008-01-15
Open Nautilus in your failsafe session and then click "View Hidden Files" in the view menu (or press control-H).
Then delete all the folders with .gnome in the name.

---

### Post by sumguy231 on 2008-01-15
You might try looking at the X log from the failsafe session. Type this in the terminal:
```
cat /var/log/Xorg.0.log
```
Look for error output and maybe post it here.

Edit: By the way, be aware Blutack's suggestion will remove Gnome configuration files, though it could work.

---

