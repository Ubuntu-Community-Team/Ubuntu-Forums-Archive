---
title: "How to remove hover comments on the Ubuntu Desktop"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gkokaisel on 2007-03-09
Ok, I find those little yellow boxed hover comments on the desktop to be annoying. I don't need them, I know what window I am pointing to or what Icon I am about to click on, so I don't need a mouse hover comment to tell me. How do I remove these? Is it even possible? I know its not a priority but if someone happens to stumble upon this, your input is much appreciated.

---

### Post by Stephen Howard on 2007-03-09
You don't say which desktop you're using, but on KDE tooltips (I think that's what you're referring to) can be turn on/off from the Control Centre | Desktop | Behaviour screen.  No idea where its done on Gnome.

---

### Post by qamelian on 2007-03-09
If you are using Gnome, press Alt-F2 to get the Run box and type in "gconf-editor", then press Enter. When the gconf-editor appears, navigate in the tree on the left to /apps/panel/global/ and locate the setting tooltips_enabled in the setting to the right. Remove the checkmark beside tooltips_enabled and exit gconf-editor. Shazam - no more tooltips!

---

### Post by gkokaisel on 2007-03-09
wOOt! thanks a bunch to both of you. I am using gnome by default, but I have kde also.

---

### Post by gkokaisel on 2007-03-09
Actually, that removed all tool tips but the nasty little buggers over the minimized apps and windows on the bottom panel.....oh boy I hate tool tips with a passion hehe. Was searching in the windows list area on the gconf-editor but no such luck.

---

