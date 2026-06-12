---
title: "Help Uninstalling a program(seamonkey)"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-03-01
I installed Seamonkey wrong so I am trying to uninstall it and there is nothing in add/remove or the synaptic packages so I was just trying to do it manually and delete the folder in usr/local/seamonkey but it says I can't since I do not have permission since I am not owner. Which I am owner. And wont let me change permissions. Here is a screen:



So if someone can help me uninstall this I would appreciate it.

---

### Post by spiderbatdad on 2008-03-01
Run ```
gksu nautilus
``` for graphical root file browser. In the future use "checkinstall" when installing packages to have them included in synaptic for easy removal.

---

