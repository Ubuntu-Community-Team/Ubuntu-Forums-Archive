---
title: "gedit -cannot display-"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by brooklynlou on 2006-03-10
Greetings all,

I'm trying the following command:

sudo gedit /etc/fstab

and I get the following reply.

(gedit:7728 ): Gtk-WARNING **: cannot open display:

what am i doing wrong?

---

### Post by taurus on 2006-03-11
Are you running that command from a console or from a terminal under X?  Why not try
```

sudo nano /etc/fstab

```

---

### Post by brooklynlou on 2006-03-11
When I run it from the terminal it works fine .. Thanks

---

### Post by Pragmatist on 2006-03-11
> Are you running that command from a console or from a terminal under X?
What is the difference between a console and a terminal.  You don't mean a virtual console do you?  Because if your in a VT your not running X and gedit is an X app

Also, brooklynlou, is your problem solved?

---

