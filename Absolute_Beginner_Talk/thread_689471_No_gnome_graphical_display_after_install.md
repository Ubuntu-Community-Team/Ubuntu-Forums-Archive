---
title: "No gnome graphical display after install"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by supersk on 2008-02-06
Trying to install Ubuntu Gutsy 7.04 on a Dell Optiplex GX620.  The GX620 has the Integrated Intel Media Accelerator 950 graphics option.

I am able to complete the installation of Ubuntu without any errors.  And I am able to see the initial login screen.  However, after I login, I just see a black display.  The Gnome Desktop never reappears.

I've already tried doing: **sudo dpkg-reconfigure xserver-xorg** without any success.

Thanks for any suggestions to resolve this issue.

---

### Post by jken146 on 2008-02-06
Type ```
startx
``` and see if that gets you going, or if it gives you any errors.

---

### Post by supersk on 2008-02-06
That didn't give me errors.  I reach the login screen and it displays fine.

I'm able to enter my username and password and ubuntu accepts it.

Then it just kind of blinks a few times and all I see is a black screen.

I'm not sure if this problem is related to X because if it was why am I am able to see the login screen correctly but not the gnome desktop manager itself?

Very weird problem.

---

