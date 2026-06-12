---
title: "Xfce menu noit working"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2006-07-12
yea it acts like it works...like it goes depressed but the menu dosnt come up

---

### Post by Kilz on 2006-07-12
> **notjohn101 said:**
> yea it acts like it works...like it goes depressed but the menu dosnt come up

[Its a known issue with a fix.]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361") Most of the time it happens when people use the Menu editor. Type this in the terminal.
```
sudo rm ~/.config/xfce4/desktop/menu.xml
```
Then reboot.

---

### Post by notjohn101 on 2006-07-12
ok but weres ~/.config/xfce4/desktop/menu.xml?

".config" isnt on the fileing system part

---

### Post by chickengirl on 2006-07-12
Just type rm ~/.config/xfce4/desktop/menu.xml in a terminal. .config is a hidden folder in your home directory. It wouldn't show up in Nautilus/Thunar unless you have it set to show hidden files. Speaking of Nautilus, if you accidentally launch it it might override xfdesktop causing the desktop menu to not work. Either don't use it at all (use Thunar instead) or edit its shortcut to add --no-desktop to the command.

ETA: actually, you don't need to use "sudo" for the rm command because the file is in your home directory.

---

### Post by wolfmaniac on 2006-07-12
this will address your problem. me too faced a similar one
> 
[http://ubuntuforums.org/showthread.php?t=198302](http://ubuntuforums.org/showthread.php?t=198302)

---

