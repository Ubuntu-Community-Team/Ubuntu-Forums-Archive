---
title: "weird flash message after install please help"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by aiphergott on 2008-04-09
Whenever i try to install flash it downloads goes to install and then i get this message anyone know how to help

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by fastTalker on 2008-04-09
I assume you installing the .deb package through apt.  I believe if adobe updates the flashplayer it breaks the .deb package because the .tar.gz file has the same name but a different minor version number (and thus different contents).  This will cause the md5sum to not match.   If you wait the the flash player package will probably be updated soon.  You can download and install it manually for now though.

---

