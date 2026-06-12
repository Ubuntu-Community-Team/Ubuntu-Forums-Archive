---
title: "I don't want X11 to start."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by fearpi on 2007-07-05
That's it, really. I don't want X to start automatically on boot. How do I accomplish that?

---

### Post by w4ett on 2007-07-05
Boot into recovery mode (command line)

---

### Post by fearpi on 2007-07-05
Well, yeah, I guess I could do that, but doesn't that prevent all my background services from being started? I want to know where it is defined that X should start automatically.

---

### Post by aquavitae on 2007-07-05
In your system settings, go to startup services, and disable xdm.  There's also a commandline way of doing this, but I'm not sure what it is.  It think its update-rc.d - you might have to install it first though.

---

### Post by houstonbofh on 2007-07-05
I think 'sudo dpkg-reconfigure gdm' might be just what you are looking for.  Play with care.

---

