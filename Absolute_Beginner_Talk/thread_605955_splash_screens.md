---
title: "splash screens"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by lattmau on 2007-11-07
I see so many different customizations for splash screens.  Can someone describe these and what order they appear (according to the default installation of ubuntu)?  And how to customize each one? 

-Gnome splash
-usplash
-GRUB splash

And are these the only ones?  Are any of them dangerous to modify?

---

### Post by markharding557 on 2007-11-07
> **lattmau said:**
> I see so many different customizations for splash screens.  Can someone describe these and what order they appear (according to the default installation of ubuntu)?  And how to customize each one? 

-Gnome splash
-usplash
-GRUB splash

And are these the only ones?  Are any of them dangerous to modify?

[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

---

### Post by lattmau on 2007-11-07
I've looked through that already.  I wanted something more specific...

---

### Post by erginemr on 2007-11-07
> **lattmau said:**
> I see so many different customizations for splash screens.  Can someone describe these and what order they appear (according to the default installation of ubuntu)?  And how to customize each one? 

-Gnome splash
-usplash
-GRUB splash

And are these the only ones?  Are any of them dangerous to modify?

1. GRUB splash: is the first one you see as soon as your computer boots, with a menu to choose from Linux, Linux Safe Mode and Windows (if you have it).

2. Usplash: is the second one you see after you choose Linux form Grub, with the Ubuntu logo and an orange progress bar.

3. Gnome splash is the third one, the small rectangular window you see after you login into Gnome.

---

### Post by lattmau on 2007-11-07
is there anything that disables the Gnome splash?  

After I installed nvidia legacy driver and nvidia-xconfig, I no longer see the Gnome splash.  Instead, after I login, it would show a black screen and my cursor becomes a white (i think its white) **X**. 

I installed gnome-splashscreen-manager to change it.  After I selected and activated a .png for my splash screen, I rebooted to see if it would work.  Right after the GRUB menu, I would get this message

> [18.279936] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Has anyone else encountered the black screen w/ the X cursor?  Does nvidia legacy and/or nvidia-xconfig disable the Gnome splash?

---

### Post by por100pre1 on 2007-11-07
Check if Startup Manager does the task:

```
sudo apt-get install startupmanager
```

You can change Usplash screens and GRUB splashes with it.

---

