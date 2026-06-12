---
title: "Documents icon on desktop"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by geneiros on 2007-01-17
hi there....


i read that is possible to put my computer, home and trash on desktop as icons. When i go to gconf-editor i see that there is also a documents icon. What is this? is a shortcut to where? Can i configure a documents folder on home like photos folder on f-spot?

thank you...

---

### Post by riven0 on 2007-01-18
From what I know, your /home directory *is* your documents directory. You can add a folder manually, and transfer all your text documents there, but I don't think there is an automatic way to do this.

---

### Post by ardchoille42 on 2007-01-18
> **geneiros said:**
> hi there....


i read that is possible to put my computer, home and trash on desktop as icons. When i go to gconf-editor i see that there is also a documents icon. What is this? is a shortcut to where? Can i configure a documents folder on home like photos folder on f-spot?

thank you...

Create a Documents directory in your home directory (ie, /home/USERNAME/Documents) and make sure the "D" in Documents is upper-case. Then open Applications -> System Tools -> Gconf editor and go to apps/nautilus/desktop and check the icons you want to appear on your desktop.

The reason you go to nautilus in gconf is because nautilus manages the desktop.

---

### Post by DarinB on 2008-03-28
my config editor in gutsy is missing 
documents_icon_name       <no value>
is this why it won't show on the desktop when i click 
documents_icon_visible           ??????????????????????

---

