---
title: "help, I lost my desktop...."
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by kurty on 2006-08-07
I made the mistake of changing my screen resolution during an update of all apps by update manager. No after  I login at the logon screen the background goes brown, now desktop or taskbar or apps come up, I just have a pointer.

Is there a way to re-install gnome from the command line (recovery mode) or to get my old settings back? 

I don't have a backup and I am worried about reinstalling the whole thing incase a lose some data.

---

### Post by Kobalt on 2006-08-07
Hello,
I don't think you need to re-install Gnome. I think you just messed up your xorg configuration file. To make it work properly again, and by the way configure your screen resolutions as you want, type this in a command line : 
```
sudo dpkg-reconfigure xserver-xorg
```

Cheers !

---

