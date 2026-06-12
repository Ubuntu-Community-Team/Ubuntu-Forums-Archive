---
title: "Ubuntu 6.06 Server no graphical login"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Formiga310 on 2006-07-24
Hi, I am a really new user to Ubuntu.

I've install version 5x with my windows and everything was fine, when I decided to format the drive and get rid of windows to install version 6.06 I came up with this problem.

I've install version 6.06, it seems that the installation went smooth, except that **I can't get to the graphical login screen**, only the text prompt. I can login and type commands, but that's it. Maybe I am missing something?

thanks for any input, I was exiting that I would finally get rid of windows but this is a little bit frustrating.

---

### Post by T700 on 2006-07-24
The server does not have a graphical interface.  You can install one, if you like.   At the command prompt type:

```
sudo aptitude update
```

Press Enter, then:

```
sudo aptitude install ubuntu-desktop
```

Press Enter.

Did you intend to install a server or will you be using this for a workstation?  If a workstation, I'd suggest you reinstall with the desktop version.  It will include many more apps that make it more suitable.

Paul

---

### Post by Formiga310 on 2006-07-25
Thanks Paul, I've installed the workstation instead of the server
Ubuntu rules!

---

