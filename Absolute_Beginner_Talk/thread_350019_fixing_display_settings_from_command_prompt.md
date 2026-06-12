---
title: "fixing display settings from command prompt"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Foudre on 2007-01-31
Well about a week ago i tried to setup my laptop on doing the dual screen setup ending up changing the wrong thing, and now i can't access kde, so if any knows how i can re set up the display  from the command shell, or some other way to get it back to normal, other then reinstalling and formating my drive, since i went thru alot customizing it and all and setup.

---

### Post by taurus on 2007-01-31
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Foudre on 2007-01-31
thx, i'll reboot and try that then.

---

### Post by jeduan on 2007-01-31
You don't need to reboot. 
When it has been done you can do 
```
sudo /etc/init.d/gdm restart
```

---

### Post by bustanil on 2007-01-31
The display configuration file is located at** /etc/X11/xorg.conf **. You can manually edit this file to configure your display, although I think it's a kludge.

---

### Post by bustanil on 2007-01-31
The display configuration file is located at** /etc/X11/xorg.conf **. You can manually edit this file to configure your display via console, although I think it's a kludge.

---

### Post by Foudre on 2007-01-31
it work ish. i can get to my dekstop but everything is all skipy an low frame rate, don't notice it untill i try to watch a video though, or start beryl. At least i can get to it now, i'll have to try to reinstall the video drivers tommorow, for my card though tommorow thx, and i said i would restart cause i had to use windows to post the question.

---

