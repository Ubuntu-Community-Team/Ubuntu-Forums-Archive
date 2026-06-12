---
title: "Compiz"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Zotick on 2008-03-15
What do I press to switch my desktop into a cube formation? I have Compiz already on my system.

---

### Post by joshrobinson on 2008-03-15
right click the desktop switcher in the bottom tray, and click preferences, make sure its 4 in the columns section

```
ccsm
```
then make sure desktop cube plugin is checked, and cube rotate is checked

---

### Post by vishzilla on 2008-03-15
I guess its the Ctrl + Alt + Button 1 of the mouse

---

### Post by Zotick on 2008-03-15
```
ccsm
```
then make sure desktop cube plugin is checked, and cube rotate is checked[/QUOTE]


It doesnt show that on my prefrences, it just shows the workspaces.

---

### Post by badmedic on 2008-03-15
Do you have CompizConfig Settings Manager installed? If not, you should install it to access all the different Compiz Fusion settings.

---

### Post by joshrobinson on 2008-03-15
> **Zotick said:**
> ```
ccsm
```
then make sure desktop cube plugin is checked, and cube rotate is checked


It doesnt show that on my prefrences, it just shows the workspaces.[/QUOTE]

i guess you misunderstood me a bit, after you set your work spaces to 4 click on close
then open a terminal and type
```
ccsm
```

then check desktop cube, and rotate cube so they have a check mark next to them

close that window, and use ctrl+alt and left or right on the arrows to rotate
or ctrl+alt and click and hold your mouse button 1 and drag to rotate

---

### Post by vishzilla on 2008-03-15
You have to install the CCSM from the repo. Go to App-> Add/Remove-> Search for 'ccsm' and install it right away.
After installation go to System-> Prefs-> Advanced Conpiz Config and then check if the Cube is enabled

---

### Post by Zotick on 2008-03-15
It keep saying this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by PmDematagoda on 2008-03-15
> **Zotick said:**
> It keep saying this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Do as the error message instructed:-
```
sudo dpkg --configure -a
```
and then try installing the package again.

---

### Post by Zotick on 2008-03-15
Thanks guys! I really appreciate your help. :)

---

### Post by agaudio on 2008-03-16
Just a tip, instead of pressing CTRL-ALT-button 1 on the mouse, you should be able to press and hold the mouse wheel to get the cube as well. Works for me.

---

