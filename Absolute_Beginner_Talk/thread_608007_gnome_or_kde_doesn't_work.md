---
title: "gnome or kde doesn't work"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Willye on 2007-11-09
hi all my friends, who can give me a hand with this, i installed ubuntu 7.10 by console, this process finished well, when i tried to star gnome or kde i couldn't, these pakages weren't installed, then i ran, aptitude install kubuntu-desk, this command installed a lot of pakages, after that i tried to run startx and appeared this error X: cannot stat /etc/X11/X (no such file or directory) aborting xinit:server error.
I need to work with the graphic part thakns a lot    :guitar:

---

### Post by aysiu on 2007-11-09
> **Willye said:**
> then i ran, aptitude install kubuntu-desk These are the commands you should run, in this order: ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start
```

---

### Post by Willye on 2007-11-09
my friend, i tried to run that but appeared this message:

package xserver-xorg is not installed and no info is available.
i installed ubuntu 7.10 server edition, will be this the problem?
tkx :popcorn:

---

### Post by aysiu on 2007-11-09
Theoretically, *kubuntu-desktop* should install Xorg, but we can manually install it just in case: ```
sudo apt-get install xorg kdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start
```

---

