---
title: "Add/Remove"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-08-18
For some reason my Add/Remove Button is gone. Any way to get it back?

---

### Post by overdrank on 2007-08-18
> **Armman said:**
> For some reason my Add/Remove Button is gone. Any way to get it back?

Hi right click on applications and select edit menus, then you can add it there. :popcorn:

---

### Post by Armman on 2007-08-18
For some reason it's not there.

---

### Post by Jimmyfj on 2007-08-18
Have a look in /usr/share/applications ?

---

### Post by por100pre1 on 2007-08-18
Follow Overdrank's instructions. Once in the Main Menu Window Click Aplications in the Menu List. It should be in the Elements list.

---

### Post by Armman on 2007-08-18
I don't know I checked there again and I'm sure of it that it's not there.

---

### Post by por100pre1 on 2007-08-18
Let's make a new one then.

Press the New Element button. A new window will appear, let's fill it out.

Name: Add/Remove

Command: /usr/bin/gnome-app-install

Comment: Install and uninstall applications.

Icon: /usr/share/icons/hicolor/scalable/apps/gnome-app-install.svg

---

### Post by Armman on 2007-08-18
I fixed it by typing "sudo apt-get install gnome-app-install" Thanks for the help.

---

