---
title: "I Need Some Help For School"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by GuitarRocker2562 on 2007-10-27
You see, I am doing my science fair project on "Which linux window manager boots the quickest?" Now I can substitute linux with ubuntu probably. Anyway, I need to know, when installing a gutsy command-line system, exactly which programs are installed, is there a list? Also, if you have any input,t hat would be great.

---

### Post by llamakc on 2007-10-27
Do the legwork by installing Gutsy server, then install xserver-xorg. Next install different window managers. TWM or OpenBox has to be near the top. Maybe RatPoison?

BTW, to see what packages are installed you can run (from the command line) `dpkg -l`. To take that information and redirect it to a file, `dpkg -l > packages.txt`.

---

### Post by GuitarRocker2562 on 2007-10-27
thanks, and one last question, does openbox, icewm, fluxbox, FVWM-Crystal, XFCE, gnome, and XDE seem like good choices (I know gnome and kde are not fast, but they are popular and I would like to test them.) And to test I want to make something appear on the screen when the system is booted, so that I have a common size for the wm being done booting, is there a way to achive this for when the wm is totally booted?

---

### Post by taurus on 2007-10-27
If you want to be fair, install the server version first.  Then install one window manager and see how long it does take to boot and how much space it takes up.

Then, reinstall the server version again, reformatting all the partitions so you would have a clean system,  and install another window manager.  

Repeat this process for all the window managers you want to test out.  

It would take a little time since you need to spend time doing your homework/assignment.

---

### Post by PPAAUULL on 2007-10-27
Is this actually considered a science fair project? Seems like you are pushing it although it would be a good idea to get linux out there.

---

### Post by GuitarRocker2562 on 2007-10-27
Yea, I have to do a clean install each time and wirte down the procedure, and yes, it is a science fair topic, my eacher is so strict about them too, it qualifies because it ony tests one dependent variable, There are independent variables and I guess the control is the boot time withot a window manager.

---

### Post by PPAAUULL on 2007-10-27
lol then he doesn't know to much about computers I am guessing?

---

### Post by GuitarRocker2562 on 2007-10-27
me, I do.

---

