---
title: "intel mac mini widescreen help"
date: 2007-07-23
forum: Apple Intel Users
---

### Post by smiles007 on 2007-07-23
hey i'm still new to linux and i installed the program 915resolution and i can get my comp to use the widescreen when i enter the command 

sudo 915resolution 3c 1680 1050  

i restart the xserver but when i shut down my computer or restart it i have to re enter the command and restart the xserver is there a way to make it always be in widescreen?

---

### Post by jonny on 2007-07-24
You can edit the file /etc/default/91resolution.  It's pretty well commented so your shouldn't run into too much trouble.

---

### Post by Gen2ly on 2007-07-24
If it's not a standard resolution and written into the driver a modeline may needed to be entered into xorg.conf.  xorg drivers cannot probe monitors, lcds... of unknown resolution.

---

