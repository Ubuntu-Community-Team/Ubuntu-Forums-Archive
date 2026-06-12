---
title: "Restart ubuntu to the command line?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-08-23
Is it possible?

---

### Post by Jimmyfj on 2007-08-23
It is - Just hit Esc when you see the Message "Grub loading stage 1.5 and chose failsafe mode option for you kernel version. Only way I know of.

---

### Post by S-AVR on 2007-08-23
if you just want the CLI and not to reboot use this: <CTRL><ALT><Fn> where n is from 1 to 6. F7 is the GUI.

---

### Post by bvmou on 2007-08-23
If you just want a command line SAVR's suggestion is the best, if you actually want to stop gnome the command is 'sudo /etc/init.d/gdm stop', that will leave you with the command line interface.  'sudo /etc/init.d/gdm restart' will restore it.  I think the KDE equivalent would just substitute k for g in the above

---

