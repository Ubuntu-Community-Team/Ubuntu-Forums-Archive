---
title: "Question about Synaptic"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by CharlieRC on 2007-04-27
I selected a package in Synaptic that I wanted to install "partimage" and completed the install. I checked the properties on partimage after the install and it indicated the package was installed and the location was System /Administration (universal).  I can't find the program anywhere on my desktop in order to execute it.  I have looked under every tab including System/Administration. What am I missing here? I am new to Linux so please don't assume anything.

---

### Post by Happy_Man on 2007-04-27
You might want to restart X (ctrl-alt-backspace) for it to appear. Some programs are finicky like that.

---

### Post by Bachstelze on 2007-04-27
Please do

```
sudo /etc/init.d/gdm restart
```

instead of Ctrl+Alt+Backspace to restart X.

---

### Post by AlexenderReez on 2007-04-27
nope....if want to appears it gnome panel ...just restart gnome-panel
> killall gnome-panel

---

