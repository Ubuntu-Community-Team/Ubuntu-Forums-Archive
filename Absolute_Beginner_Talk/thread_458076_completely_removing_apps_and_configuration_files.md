---
title: "completely removing apps and configuration files"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-29
I was running mythtv, changed the resolution and can not see anything but giant letters which means I can not navigate to change the resolution back to normal. I want to completely remove the program including the configuration files. I noticed in the /home/USR/ directory there are some hidden .mythtv, .beryl, etc files. Would deleting these do the trick? If I use synaptic to uninstall, these files remain and when I do a reinstall of mythtv, I still get the same problem with the resolution set to like 500x300. SO how do you completely remove all traces of a application including user configurations?

---

### Post by cymen on 2007-05-29
```
sudo apt-get --purge remove <application>
```

Give that a whirl - the purge option removes configuration files too. If things are still left, then you can try deleting them manually.

---

### Post by jba6511 on 2007-05-29
did that but it still left the .mythtv folder so I manually deleted that. I just did a search and there are severla instances of mythtv left over. How can I remove them automatically.

---

### Post by aroch1 on 2007-05-29
rm -rf .mythtv

---

