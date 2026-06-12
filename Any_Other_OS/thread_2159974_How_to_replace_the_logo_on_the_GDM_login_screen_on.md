---
title: "How to replace the logo on the GDM login screen on Arch Linux"
date: 2013-07-05
forum: Any Other OS
---

### Post by owemeacent on 2013-07-05
I have an Arch Linux system that I made a couple days ago. When I used to use Fedora, the Fedora Logo appeared on the GDM login screen. How can you put the Arch Linux logo on though

---

### Post by Irihapeti on 2013-07-05
*Thread moved to **Other OS/Distro Support**.*

---

### Post by slickymaster on 2013-07-05
See this: [https://bbs.archlinux.org/viewtopic.php?id=114683](https://bbs.archlinux.org/viewtopic.php?id=114683)

---

### Post by fantab on 2013-07-07
GDM is not as configurable as it used to be. You can try [Slim display manager]("https://wiki.archlinux.org/index.php/SLiM"). 

Or with GDM, you use a background of your choice with the logo of your choice. 
The background file for GDM is located at /usr/share/gnome-shell/theme/noise-texture.png. Just copy your background file (.png) and rename it as 'noise-texture.png'. You just rename the original file as 'noise-texture.png.bak. 
Or you can just add a logo on original file. 
Remember any update to gnome-shell will replace your background with the original. So you have reset it after every shell update.

My two cents...

---

