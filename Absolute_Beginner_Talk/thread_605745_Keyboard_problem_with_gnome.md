---
title: "Keyboard problem with gnome"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by pasoderholm on 2007-11-07
Hello!

I have the following problem: 
At the GUI login some keys on the keyboard don't work (are inactive). If I log in with the console everything works fine. 
I'm using ubuntu 6.06 LTS, and it worked fine until today when I run dpkg-reconfigure xserver-xorg to setup for a new monitor.

I have the keyboard, mouse and screen connected to a "black box" switch but it has never been any trouble with that before, and the keyboard works fine with my other ubuntu box as well as with a Windows XP box. And as I mentioned, it works fine when I log in with the console, and works well if I use a openssh terminal from another box.

Any advise?

-Paul

---

### Post by Daveth on 2007-11-07
did you make a copy of the xorg.conf file before you changed it? If you did it might be better to return to that and try to manually edit the parameters to get your monitor to play nicely, rather than attempt to re-build it which looks a bit like it might have broken something.
Just an idea:)

---

