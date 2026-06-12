---
title: "Is restart necessary after xorg.conf change?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by maaronB on 2006-09-25
I have just changed some of the values in xorg.conf.
To get them to take effect do I have to do a complete reboot, or can I just restart X, or is there something I can do at tty1, or anything like that?

---

### Post by nudnik on 2006-09-26
Restarting X should be enough.

---

### Post by pistcivet on 2006-09-26
Ctrl-Alt-Backspace
should restart the X-server.

---

### Post by henriquemaia on 2006-09-26
But you can test your new configurations doing a:

```
sudo xinit -- :2
```

You'll get a new X session. To exit it, press ctrl+alt+backspace. You'll be taken back your your remaining X session. This is a good trick for changing and testing configurations on the X server without loosing a GUI for doing it.

---

### Post by drr422 on 2006-10-23
I never new that trick:
sudo xinit -- :2
Thanks that will help me out alot.

---

