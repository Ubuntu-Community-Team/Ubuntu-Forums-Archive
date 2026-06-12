---
title: "Login Error!!"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by milad on 2007-04-22
Here is the message I get when i try to login to my Ubuntu:

**Your session only lasted less than 10 seconds. If you have not logged out urself, this could mean that there is some installation problem or that you may be out of diskspace. Try loggin in with one of the failsafe sessions too see if you can fix the problem.**

and here is the details:

[B]/etc/gdm/PreSession/Default: Registring you session with wtmp and utmp
/etc/gdm/PreSession/Default: Running /usr/X11R6/bin/sessreg -a -w /var/run/utmp -x  "/var/lib/gdm/:0.Xservers"-h "" -l '":0 "milad"

/etc/gdm/Xsession: beginning session setup ...
mkdtemp: private socket dir: No space left on device[/B]

The Gnome Fail safe gives the same error but i am able to use Terminal fail safe

Does anybody know what have caused this and how i can fix it??

This Feisty version hasn't been as good as i hoped!!l

---

### Post by marko_4454 on 2007-04-22
I am not claiming to be an expert, but you should try in the terminal something like this to reconfigure your Xserver which is the one that seems to be giving you problems.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by milad on 2007-04-22
isn't there an easier way to restore default settings?

---

### Post by marko_4454 on 2007-04-22
If you have a backup of your xorg.conf file, just overwrite your old one with your new one. But besides that, I dont know any other method. Why do you ask? Do you have something you dont want to lose, aka Beryl?

---

