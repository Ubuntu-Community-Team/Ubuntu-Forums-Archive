---
title: "desktop effects ?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-20
when I use the live CD the desktop effects work but in the installed version the desktop effects dont work. When I go to the menu and try to turn them on it displays an error message saying" desktop effects could not be enabled". Does this mean my graphics card does not support the desktop effects? keep in mind that the effects do work with the live cd

---

### Post by forestpixie on 2008-03-20
you need to install the graphics card first - have you done that - try using restriced driver in system>admin

you will also need to install the settings manager, open a terminal

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by mahela007 on 2008-03-20
the restricted driver thing says that my hardware does not need any restricted drivers.

---

### Post by erginemr on 2008-03-20
What is your the brand of graphics card, and the output of the following command:
```
lspci | grep -i vga
```

---

### Post by mahela007 on 2008-03-20
brand is ATI.
how do I input the command.?
I'm a newbie

---

### Post by sayakb on 2008-03-20
If it is an ATI, it should require restricted drivers. Generally Intel GPUs don't need restricted drivers.

---

### Post by erginemr on 2008-03-20
> **mahela007 said:**
> brand is ATI.
how do I input the command.?
I'm a newbie

You need to open Gnome terminal from Main Menu -> Applications -> Accessories -> Terminal,
post the above command there, select the outcome with your mouse, right-click, select copy and post it here.

---

