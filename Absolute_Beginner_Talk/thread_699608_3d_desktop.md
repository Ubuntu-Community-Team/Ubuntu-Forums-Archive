---
title: "3d desktop"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by umontu on 2008-02-17
Ok i just got ubuntu 7.10 love it btw
Im new to ubuntu but Ive used other linux os's before but i wanted to know how to get the 3d desktop switcher. Iooked round and all the advice i found was for other versions and the closest thing i found was telling me to look at a menu that didnt exist

---

### Post by Arthur Archnix on 2008-02-17
You need to install compizconfig-settings-manager
```
sudo apt-get install compizconfig-settings-manager
```
Enjoy.

---

### Post by RomeReactor on 2008-02-17
Hi. Do you want to enable the cube? Just as a comment on Arthur Archnix's reply, once you have compizconfig-settings-manager installed (either through Add/Remove, Synaptic or the terminal) you can find it in 'System->Preferences->Advanced Desktop Effects Settings'. Open it, and on the 'Desktop' section, uncheck 'Desktop Wall' and check 'Desktop Cube' and 'Rotate Cube'. Also, press the 'General Options' button (first one on the top), go to the third tab (Desktop Size) and increase the 'Horizontal Virtual Size' to four.

---

### Post by umontu on 2008-02-17
hey thanks but ive done that and set to work but its not doing when i press the keys
do i need to restart?

---

### Post by RomeReactor on 2008-02-17
No, a restart is not needed. Do you have Compiz enabled? What video card do you have?

---

### Post by umontu on 2008-02-17
Nvidia geforce 6200

whats compiz (god im a noob sorry) *edit I know what it is but how do you mean enabled isnt it already?

---

### Post by RomeReactor on 2008-02-17
Compiz is the window manager that lets you use 3D effects, such as the cube. Do you have the nVidia drivers installed? If you're unsure, go to 'System->Administration->Restricted Drivers Manager ' and check the box for your card. You can then enable the effects in 'System->Preferences->Appearance', go to the 'Visual Effects' tab and select 'Normal'.

---

### Post by Yes on 2008-02-17
It's what generates the cube, along with a bunch of other cool effects that you can configure in 'System->Preferences->Advanced Desktop Effects Settings'.

Go to System -> Preferences -> Appearence, and then the Visual Effects tab and select "custom", and it should be working.

---

### Post by umontu on 2008-02-17
Yep they're all installed fine

---

### Post by RomeReactor on 2008-02-17
Press (and hold) CTRL+ALT and the left mouse button, and move the mouse to the left or right. Does the cube show up? If not, please open a terminal (Applications->Accessories->Terminal) and write or paste:
```
glxinfo | grep rendering
```
Press ENTER and post the output.

---

### Post by umontu on 2008-02-17
> **Yes said:**
> It's what generates the cube, along with a bunch of other cool effects that you can configure in 'System->Preferences->Advanced Desktop Effects Settings'.

Go to System -> Preferences -> Appearence, and then the Visual Effects tab and select "custom", and it should be working.

ermm nope already on

---

### Post by Ivorydawn on 2008-02-17
Hi,

Have a read of this, it will get you up and running.

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Regards

Andrew

---

### Post by umontu on 2008-02-17
wow that one worked thanks a lot

---

