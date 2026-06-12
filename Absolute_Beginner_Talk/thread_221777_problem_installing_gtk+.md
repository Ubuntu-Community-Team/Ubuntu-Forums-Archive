---
title: "problem installing gtk+"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Micik on 2006-07-24
Hello
I'm having problems installing gtk+ on my ubuntu 6.06 LTS machine.
I have downloaded atk, glib cairo and pango. These are the dependencies that are stated for gtk+.
However during configurations (./configure) I get error message that X development libraries are not present. Please can you give me advice about these X libraries and suggest me link where I can find and download them?

Thanks

---

### Post by jordilin on 2006-07-24
If I'm not wrong gtk+ goes by default in Ubuntu, since it uses Gnome. Which package are you talking about exactly?

---

### Post by Micik on 2006-07-24
Well when I try to install anjuta, it fails because of gtk+. I'm trying to install gtk+-2.8.17 exactly

---

### Post by gingermark on 2006-07-24
anjuta is in the repositories. Do ```
sudo apt-get install anjuta
```
I'm guessing you were trying to compile it. You'd need the development libraries for Gtk to do so - they are also in the repositories.

---

