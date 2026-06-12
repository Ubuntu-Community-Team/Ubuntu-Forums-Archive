---
title: "reseting resolution"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-14
I tried changing my resolution for my monitor but when i restarted my computer and after the boot screen loaded my monitor went blank then had the following message of something like resolution to high or not supported.

is there a way I can rest the resolution?

I can't see anything so i can't just go into my files and do it that way.

---

### Post by RyviusRan on 2008-03-14
bump

---

### Post by joshrobinson on 2008-03-14
either restart in recovery mode, or hold cntrl+alt+f1 to get to a terminal

```
sudo dpkg-reconfigure xserver-xorg
```

run that, select your video driver, your resolution etc.

---

### Post by sailor2001 on 2008-03-14
ctrl/alt/f1 on boot up and type in "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by RyviusRan on 2008-03-14
thanks that worked.

but when I go into my setting for changing my monitor i can't find my monitor in it.

Compaq FS7600

is there any place where I can download the right ones to add to my settings, because now I can't  get the cube setting to work or more than 2 desktop screens to work.

---

### Post by RyviusRan on 2008-03-14
does anyone know?

---

### Post by RyviusRan on 2008-03-14
my monitor is stuck in plug in play as auto detect.

also i can't locate my monitor type in settings is there a way I can download it. becuase under compaq they don't have the fs7600 as a choice.

also my desktop effects aren't working.

---

