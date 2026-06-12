---
title: "Keybinding issues: Metacity and Open Office"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by evanvlane on 2006-12-15
I've been trying for the past few days to get polytonic Greek support in Open Office, and have been told I'm pretty much down to making individual macros for each of the diacritical combinations. 

I've assigned each macro to a key combination (eg. <Ctrl><Alt>h for &#8134;) but I also have Metacity bindings (<Ctrl><Alt>h = /home/elane).

Is there a way to make MetaCity disable itself every time I load open office? Or even better, only when the Open Office window has focus?


Evan.

---

### Post by evanvlane on 2006-12-15
Any pointers?

---

### Post by simosx on 2006-12-19
> **evanvlane said:**
> Any pointers?

If you can read modern Greek (or follow the screenshots), see
[http://simos.info/blog/archives/342](http://simos.info/blog/archives/342)

There is an existing Greek Polytonic keyboard layout in Ubuntu (well, all distros). For technical reasons, if you want to use this layout in OOo, you need to open GNOME Terminal and type

$ export GTK_IM_MODULE=xim

and then

$ oowriter

The X server (Xorg) has support for Greek polytonic, but due to a still unresolved issue in GTK+, you need to do the above workaround.
Tell me if this works for you.

---

### Post by tico on 2007-06-21
This doesn't seem to work for breathings. For accents it works fine.

---

### Post by simosx on 2007-08-08
I just realised that Greek Polytonic works by default if you have enabled the Greek locale.
Thus, for most people that do not speak modern Greek, can follow a simple workaround.
Information at 
[http://simos.info/blog/archives/639](http://simos.info/blog/archives/639)

Tell me if it works for you.

---

