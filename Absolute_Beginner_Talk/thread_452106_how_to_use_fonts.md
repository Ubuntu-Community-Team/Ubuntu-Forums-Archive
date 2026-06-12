---
title: "how to use fonts"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-23
hey guys. i downloaded some fonts from gnome look but i dont know how install/use em.. where do i put em and how thanks

---

### Post by Ek0nomik on 2007-05-23
~/.fonts

That should do that trick.  If that directory doesn't exist, create it.

---

### Post by HunkieChan on 2007-05-23
i cant create folder in the file system

---

### Post by Ek0nomik on 2007-05-24
What do you mean you can't create a folder?

```
cd ~/
mkdir .fonts
```

if you don't have permission

```
cd ~/
sudo mkdir .fonts
```

---

### Post by BLTicklemonster on 2007-05-24
Make a .fonts folder in your /home/myname/ directory. Then put the fonts in there.

cd /home/myname/
mkdir .fonts

viola.


You can even navigate in nautilus to the directory, and just right click and add one if you want to do it that way.

---

### Post by HunkieChan on 2007-05-24
gracias

---

