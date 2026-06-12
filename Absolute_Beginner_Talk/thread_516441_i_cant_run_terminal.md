---
title: "i cant run terminal"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by yeahitsjames on 2007-08-03
right im completly new to linux and xubuntu. but when ever i try to run the terminal it logs me out.


what does this mean and what can i do about it??



please help

---

### Post by apswartz on 2007-08-03
Tell us how you start up terminal. Through the menu? Clicking on an icon? (Sorry, I use kubuntu, and I'm not sure of your options).

---

### Post by heimo on 2007-08-03
Yeah, give us more information. You could try to hit alt+F2 and try running xterm, and then gnome-terminal. Is the end result same?

---

### Post by yeahitsjames on 2007-08-04
well i tried the alt+F2 thing but it didnt work. no matter what type of terminal i try to run it just logs me out. ive tried "terminal" and "root terminal" and they both do the same.


has that helped???

---

### Post by Martje_001 on 2007-08-04
CTRL + ALT + F2 and login, does it work then?
And are you using 7.04 / 7.10 or older?

---

### Post by Booty on 2007-08-24
> **Martje_001 said:**
> CTRL + ALT + F2 and login, does it work then?
And are you using 7.04 / 7.10 or older?

Hello, after starting system this morning i faced same problem.
All of terminals (gnome-term, Terminal, xterm) refuses to start.
With "CTRL + ALT + F2" login promt opens, but after typing in
username and password i see standart welcome screen and string at the end:
booty-desktop - /home/bootybooty-desktop

It waits a bit of second and then displays login prompt once again:
login:

I also checked shell and home dir and permissions, its all seem correct.

syslog entry:
Aug 24 10:16:09 booty-desktop init: tty2 main process ended, respawning

auth.log entry:
Aug 24 10:16:09 booty-desktop login[5636]: (pam_unix) session opened for user booty by (uid=0)
Aug 24 10:16:09 booty-desktop login[5636]: (pam_unix) session closed for user booty

I'm running 7.04

---

### Post by eentonig on 2007-08-24
To start a command. It's not <ctrl>+<alt>+<F2>, but <alt>+<F2>

What happens when you select the terminal from Accesoires\Terminal?

---

### Post by Booty on 2007-08-24
> **eentonig said:**
> To start a command. It's not <ctrl>+<alt>+<F2>, but <alt>+<F2>

What happens when you select the terminal from Accesoires\Terminal?

Empty terminal window pops out and immediately dissappears.

---

### Post by eentonig on 2007-08-24
Ok. Open your ~/home folder. There should be some hidden files

.bashrc and .profile

remove or rename those and try again. (Best is to rename them. If it works now, we can go through those files to see what's causing this)

---

### Post by Booty on 2007-08-24
Thanks for the tip, but unfortunately it didnt help :(

---

