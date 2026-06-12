---
title: "&quot;sudo dpkg-reconfigure xserver-xorg&quot; problems"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2006-10-31
Ok, i was trying to configure xgl yesterday, and I goofed it up real bad and the computer freezes on the startup screen.

So I did the command I could answer the questions fine, until I go to the monitors color depth. When I clicked on an option, the command prompt would pop up under the config menu, saying 'overwrite of possible custom configuration file' and then it tells me to backup the file.

So is there something I need to type in the command prompt to let it continue? Nothing I've tried works.

---

### Post by ReaderRat on 2006-10-31
Backup xorg.conf first and then continue:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

