---
title: "Desktop Location"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by redbluemangle on 2006-11-19
is it possible to designate any directory as the desktop? I know theres a way to switch it between the /home/user/desktop and /home but is there a command to set any directory as the desktop? I want to set my fat32 partition to be my desktop.

---

### Post by bodhi.zazen on 2006-11-19
Try a link:

```
mv ~/Desktop ~/Desktop.bak
ln -s /path/to/fat/partition ~/Desktop
```

You may need to re-start gnome.

You can cp ~/Desktop.bak/* ~/Desktop to copy prevous icons/shortcuts.

---

### Post by redbluemangle on 2006-11-19
ahh thankyou :D

---

