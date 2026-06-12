---
title: "[SOLVED] Changing Gnome to XFCE Question"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2008-03-13
If I change my desktop enviroment from Gnome to XFCE, will I lose all of my custom menus ?

i.e. I have a single menu that contains all of my Web development apps (graphics and text editors etc). Will these vanish and need re-creating ?

Cheers in advance.

---

### Post by zxscooby on 2008-03-13
I think you can install xfce separately and choose the one you want at login.

---

### Post by kpkeerthi on 2008-03-13
No. But it may not be visible in XFCE session. You need to come back to gnome session to access your custom menu.

Select XFCE or GNOME at the login screen.

---

### Post by jan quark on 2008-03-13
off the top of my head: I think the configuration stays unaltered

just install the xubuntu-desktop and see

---

### Post by WorldTripping on 2008-03-13
OK,

So I'm using Synaptic : Edit : Mark Packages By Task...

Selected the Xubuntu Desktop (without de-selecting the Ubuntu one.)

And it tells me that it's going to remove a pile of apps, including Ubuntu-Desktop.

Is this the best way ?

(I'm not too interested in keeping Gnome, that's why I'm changing to the Xubuntu desktop.)

---

### Post by kpkeerthi on 2008-03-13
Run ```
sudo aptitude install xubuntu-desktop
``` and post the result here so it is easier to see rather than guessing at what is happening at your end.

---

### Post by WorldTripping on 2008-03-13
> **WorldTripping said:**
> 
OK,

So I'm using Synaptic : Edit : Mark Packages By Task...

Selected the Xubuntu Desktop (without de-selecting the Ubuntu one.)


I used the Synaptic method above to load the Xubuntu desktop.

It apparently did remove a couple of Gnome apps, but it mainly spent its time installing stuff.

I can now choose which session on startup.

Only thing is I now have a strange set of menu option, including some of my Gnome custom launchers.

Guess I'll have to look at this [http://ubuntuforums.org/showthread.php?t=193093]("http://ubuntuforums.org/showthread.php?t=193093") to help me tidy it all up.

---

