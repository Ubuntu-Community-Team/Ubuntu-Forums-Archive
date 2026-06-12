---
title: "Equivalent of startup folder"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-06
On Windows, there is a folder called 'startup' into which you can place executables, or links to executables, so that they run automatically after Windows has booted and fully loaded itself.

Is there an equivalent on Ubuntu Feisty Fawn 7.04 x64?

---

### Post by Lord Illidan on 2007-06-06
Certainly -> System -> Preferences -> Sessions

Enter the commands you want there.

---

### Post by steeleyuk on 2007-06-06
If you really want a folder based method (like Windows) you can add items at:

/home/<username>/.config/autostart

In your home directory press CTRL+H to show hidden folders. Open .config and autostart folders. Drop any items you want in there and they should start on next login.

---

### Post by ecs_pf5 on 2007-06-06
Excellent - thanks :)

---

### Post by djgrandmarquis on 2007-06-06
If you ever venture into KDE, the startup folder is

/home/<username>/.kde/Autostart

---

### Post by Papi-KB7VGW on 2007-06-06
Thanks from me also...  Learning alot here and it is fun doin it!

---

