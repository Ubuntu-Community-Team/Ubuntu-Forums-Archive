---
title: "trash icon"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-07-26
i want a trash icon on my desktop so it doesn't have to take up space on my panel.  is there a script i can get somewhere that will make it use a full trash can icon when something's in the trash, and an empty trash can icon when nothing's in it?

---

### Post by Kosimo on 2007-07-26
> **Niklas Schröder said:**
> i want a trash icon on my desktop so it doesn't have to take up space on my panel.  is there a script i can get somewhere that will make it use a full trash can icon when something's in the trash, and an empty trash can icon when nothing's in it?
[URL="http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/"]
HERE[/URL] the perfect easy and quick guide to do exactly what you want.


Cheers.

---

### Post by Rocket2DMn on 2007-07-26
You could probably make a launcher for a folder and direct it to /.Trash

edit: use the method above, looks simple enough :)

---

### Post by digitalbenji on 2007-07-26
Hi, I just did this for myself.  

   1.      Open the Configuration Editor, by running the program gconf-editor (see the run application manual for help on how to run an application without using the menu). (alt+f2 gconf-editor)
   2.      Choose apps->nautilus->desktop.
   3.      Turn on computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.


Taken from here:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s07.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s07.html)

---

### Post by Niklas Schröder on 2007-07-26
thanks for the tip!  :)  i can't believe i didn't think to look there.  :p  must browse through gconf-editor later...  ;)

---

