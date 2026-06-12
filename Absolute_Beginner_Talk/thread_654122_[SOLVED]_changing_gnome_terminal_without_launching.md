---
title: "[SOLVED] changing gnome terminal without launching it"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-12-30
Last night I borked my pc and today I'm reinstalling

I was trying to make a transparent terminal as per this post.
[http://ubuntu-unleashed.blogspot.com/2007/08/howto-completely-transparent-shell-on.html](http://ubuntu-unleashed.blogspot.com/2007/08/howto-completely-transparent-shell-on.html)
It worked fine last time.  This time, it crashes x server.  I set trans as the deafult profile so now I can't open the gnome terminal without crashing my x server.  I'm sure you can see the problem.

Is it possible to reset the gnome terminals default profile to "default" without launching it?

Thanks.

---

### Post by yabbadabbadont on 2007-12-30
Fire up gconfeditor and browse around for settings related to gnome-terminal.  I'll bet it is in there somewhere.

Edit: the command is gconf-editor.  Sorry.

Edit2: You need to change the following key's value: /apps/gnome-terminal/global/default_profile

Edit3: Probably you should change it to "Default", assuming that you haven't modified the default profile.

---

### Post by doorknob60 on 2007-12-30
I'm not sure, but in the meantime you could always use Konsole or xterm or something.

---

### Post by il-luzhin on 2007-12-30
Thank god,  I owe you folks... again

---

