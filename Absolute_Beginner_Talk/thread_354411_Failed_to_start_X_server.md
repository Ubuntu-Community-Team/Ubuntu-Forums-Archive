---
title: "Failed to start X server"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by dstrathman on 2007-02-05
While trying to install beryl, I was taken to the terminal and received the error message "Failed to start X server."  Whenever I boot now instead of booting into Gnome GUI, it boots into the terminal and displays the error message.  Please help.

---

### Post by dbbolton on 2007-02-05
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)


if you're fairly new, the only thing i can recommend:
```
sudo dpkg-reconfogure xserver-xorg
``` or ```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

note that 'xorg.conf.old' is just whatever your backup file is named.

---

### Post by dstrathman on 2007-02-05
Thanks for your help, I will try that

---

