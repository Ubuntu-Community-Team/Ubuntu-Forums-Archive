---
title: "Terminal code"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-11-03
Hey, I kinda messed up my display by messing up a file... is there a code that will pull up text files in the textual interface and will allow me to edit them? I have tried gedit, but apparently it tries to open the file in a window.

So as to make things less confusing, I want to open and edit this file in the terminal:
/etc/default/linux-restricted-modules-common

Thanks for all of your help!

---

### Post by mikewhatever on 2007-11-03
sudo nano /etc/default/linux-restricted-modules-common

The shortcut to save is Ctrl+o, and to exit Ctrl+x.

---

### Post by taurus on 2007-11-03
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/default/linux-restricted-modules-common
```

---

### Post by kevindubrow on 2007-11-03
Thanks a lot, you guys are great!

---

