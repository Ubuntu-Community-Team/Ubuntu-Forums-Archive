---
title: "switching to graphic mode"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by noahw on 2007-09-23
I switched to command line (ctrl+alt+shift+f1) to install an nvidia graphics driver.  Now I'm not sure how to switch back to graphic mode.  Can anyone please help?

---

### Post by bruce2000 on 2007-09-23
ctrl-alt-f7

---

### Post by mostwanted on 2007-09-23
Either restart or type

```
startx
```

and then press enter.

---

### Post by ddrichardson on 2007-09-23
If you have stopped GDM, which you need to do to configure the nVidia binary driver then```
sudo /etc/init.d/gdm start
```Is the one for you. If X is already running then use CTRL+ALT+F7

---

