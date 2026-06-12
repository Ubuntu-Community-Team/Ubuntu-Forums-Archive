---
title: "Error: Could not find Python Headers"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by arthurbarnhouse on 2006-07-29
Trying to install a program called gimmie.  DId a search in the forums and google linux, this particular error doesn't seem to happen often because I can't find some past instances.  What should I do?

Edit:

Err, I realized I didn't actually say what the error was.  It's the same as the title, "Could not find Python Headers."

---

### Post by arthurbarnhouse on 2006-07-29
bump

---

### Post by moma on 2006-07-29
Gimmie the name of your program. Do you mean?
[http://www.beatniksoftware.com/gimmie/]("http://www.beatniksoftware.com/gimmie/")  ?

"Headers" mean development (*.h) files which are conveyed by -dev packages.

$ sudo aptitude update 

$ sudo aptitude install python-dev

You may also need:
python-gtk2-dev   python-gnome2-dev    libgnome-desktop-dev  libgnomecups1.0-dev  libwnck-dev

---

### Post by arthurbarnhouse on 2006-07-29
Thanks.

---

