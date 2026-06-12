---
title: "GUI disappears when trying to install Beryl"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-06-14
I was trying to install Beryl using [this guide](http://www.arsgeek.com/?p=1313). I came upto the part where you have to press Ctrl+Alt+Backspace. When I did that, the screen went black and then I came across a DOS-like GUI that said that the interface could not be loaded due to some error (it was a different message, I'll try to get it if possible). 

Since then, my Ubuntu has not been booting up on both kernels. I don't want to reinstall Ubuntu yet, but I think the big problem is because of the xorg.conf file you have to edit. Since I can start Ubuntu is recovery mode, is it possible to edit the xorg file entirely via Terminal?

Also, I made a backup of the xorg file before modifying it. How do I replace the original file with the backup file? The backup has a .bak ending to it.

Thanks in advance. :)

---

### Post by Outrunner on 2007-06-14
Boot into recovery mode and type
```

sudo cp /etc/X11/<backup_name> /etc/X11/xorg.conf
```

Good thing you made a backup!

---

### Post by Sabretooth on 2007-06-14
Thanks a bunch! Ubuntu is working perfectly well now! I'll try to remember that command.

---

