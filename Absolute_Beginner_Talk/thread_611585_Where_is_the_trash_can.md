---
title: "Where is the trash can?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by johann_p on 2007-11-13
I deleted the (GNOME) Trash-can icon from the desktop. Where else can I find it? I would have expected it in "Places" but it is not there, or anywhere else i looked.

---

### Post by robinl on 2007-11-13
Bottom right corner? Or if you've removed it just add it back to gnome-panel by right-clicking on it. Otherwise it's also in your nautilus, below all your drives.

---

### Post by Maestro23 on 2007-11-13
Also, a hidden directory in your home folder.

> /home/username/.Trash

---

### Post by bulldog on 2007-11-13
Press ALT+F2  type gconf-editor  choose apps-->nautilus-->desktop
Look at the checkboxes and check what you want on your desktop.

---

### Post by mcduck on 2007-11-13
It's a hidden directory inside your home dir, called .Trash. Press Ctrl-h to see it. If you want to use it for anything you need to add the trash icon to your desktop or to your panel.

To add it to your panel, right-click on the panel, select 'Add to Panel', find the Trash and drag&drop it into your panel.

To add it to your desktop, press Alt-F2, run 'gconf-editor', browse to apps/nautilus/desktop and enable 'trash_icon_visible'

---

### Post by johann_p on 2007-11-13
Thank you for all the tips, I have my trashcan again! :)

---

