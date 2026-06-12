---
title: "[SOLVED] desktop"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2008-03-12
could i get a walk through on how too get the 3d cube desktop too work, or something similar. and help through the process?

---

### Post by Dark Star on 2008-03-12
Ok to make your desktop get the cube effect do this.. Since you are using Ubuntu 7.10 it will be easy .. 

```
sudo apt-get install compizconfig-settings-manager
```

Open CCSM by pressing ALT+F2 and type ccsm .. It will open the settings manager .. Select the plugins you want to enable and it wil work for you.. After enabling Desktop cube plugin. Switch on Desktop effects with custom settings..

Right click on desktop .. then open Appearance under it see the tab Effects.. Select Custom.. and to use Cube plugin press **Ctrl + ALt + Mouse 1**

---

### Post by Fred_E _krugar on 2008-03-12
you can go here he has several guides on Compiz : [http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)

---

### Post by dylondadank on 2008-03-12
when i try too enable the custom effects it reads The Composite extension is not available

---

### Post by jan quark on 2008-03-12
do you have an ATI card?

if yes install this package
```

sudo apt-get install xserver-xgl
```

and change the session during login to xclient

---

### Post by dylondadank on 2008-03-12
what do you mean by change sesion to xclient?

---

### Post by dylondadank on 2008-03-12
i logged back in, and it let me enable custom effects with no error, but the 3d cube still is not working, its just a normal desktop

---

### Post by jan quark on 2008-03-12
did you have install ccsm /compiz configuration something manager?

you need 4 desktops planes and you have to hit the keys
Ctrl+Alt+Left/right Arrow or the Middle Mouse Button

just check the options in CCSM

---

### Post by dylondadank on 2008-03-12
okay, what effects should i have enabled for everything too run nice and smoothly?

---

