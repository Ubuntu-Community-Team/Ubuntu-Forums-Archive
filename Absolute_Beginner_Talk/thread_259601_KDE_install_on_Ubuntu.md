---
title: "KDE install on Ubuntu"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-17
I am using Ubuntu and would like to install KDE and any other (dont know what you call it exactly) available. Just for the sake of having alternatives. How would I do this?

Thank you.

---

### Post by Arisna on 2006-09-17
KDE and XFCE are the two main Desktop Environments available on Ubuntu other than GNOME.  To install them, enter these commands in a terminal:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop
```

The first line updates your local software index, and the following lines install KDE and XFCE desktops, respectively.  You can switch freely between the three.

---

### Post by ciscosurfer on 2006-09-17
From the repositories, you can also install edubuntu (an educational version using the GNOME desktop)```
sudo aptitude update && sudo aptitude install edubuntu-desktop
```After installing any new desktop environment, you simply need to logout and then select 'sessions' from your login screen, switch to a new desktop environment by clicking the radio button, hit ok, login with your username and password, choose 'just for this session' if you don't want this new selection to be your default, otherwise, set it as default...login to your new environment.

---

### Post by alex-desktop79 on 2006-09-17
Thank you :D

---

### Post by destromofia on 2006-09-17
ok, so I have a quick question, I also wanted to see what KDE was all about, I tried just inputting:

sudo aptitude update
sudo aptitude install kubuntu-desktop

but it didn't seem to work, when I go to log out, the log out screen just goes completly white and I have to restart.  when the log in screen comes back up, everything seems ok, but no kubuntu.

Any help?

---

