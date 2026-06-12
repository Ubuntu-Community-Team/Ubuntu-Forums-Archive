---
title: "latest ubuntu version"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-27
Is it possible to upgrade my ubuntu to the latest version?  Is the latest version stable?

---

### Post by Emerzen on 2005-10-27
Yes, but there's no guarantee that it will work w/out a hitch...theoretically it should, though most people recommend a clean install.  I would **do a back-up before proceeding**, so you can restore if all does not go well.  Here's the steps:

1.)  Change all of your apt menu.lstt from whatever version name you run to breezy.

**sudo gedit /boot/grub/menu.lst**

2.)  **sudo apt-get update**

3.) **sudo apt-get dist-upgrade**

---

### Post by Kyral on 2005-10-27
Breezy is stable now. Its the official version

---

### Post by Kapre on 2005-10-27
[QUOTE=racermike1967]Is it possible to upgrade my ubuntu to the latest version?  Is the latest version stable?[/QUOTE]

May we know what version do you have right now?

K

---

