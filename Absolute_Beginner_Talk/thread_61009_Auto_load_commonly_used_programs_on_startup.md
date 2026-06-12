---
title: "Auto load commonly used programs on startup"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by cnayak on 2005-08-30
I almost invariably use Amarok, Gaim and Opera everytime I use my laptop. Is there some way I can start up these apps automatically on bootup? I also use IceWM, so it's sort of tedious to wrie out the program names in te terminal.

---

### Post by ubuntme on 2005-08-30
go to system - preferences - sessions - startup

you can also add programs to the menu

good luck

---

### Post by cnayak on 2005-08-30
[QUOTE=ubuntme]go to system - preferences - sessions - startup

you can also add programs to the menu

good luck[/QUOTE]

  For some strange reason, double clicking the sessions icon doesn't work. all the other icons respond. any idea of whats wrong?

---

### Post by ubuntme on 2005-08-30
no idea,

Do you have administrator privlages?

what happens when you try to run from the command line, I beleive the program is gnome-session-properties

---

### Post by aysiu on 2005-08-30
[QUOTE=cnayak]For some strange reason, double clicking the sessions icon doesn't work. all the other icons respond. any idea of whats wrong?[/QUOTE] Why are you double-clicking it?

---

### Post by roots on 2005-08-31
hmmm...where would i add autostart entries for apps & prox if i don't want to use the system-preferences gui but do it manually via terminal - in something like .bashrc or init.d ???

cheers,
.roots

---

### Post by cayamara on 2005-08-31
[QUOTE=roots]hmmm...where would i add autostart entries for apps & prox if i don't want to use the system-preferences gui but do it manually via terminal - in something like .bashrc or init.d ???[/QUOTE]Here's a nice HOWTO on [Making Scripts run on boot time](http://www.debian-administration.org/articles/28). Its for Debian, but should work fine in Ubuntu, since Ubuntu and Debian both use the system V init scheme.

Note that this is for running stuff at boot time. So if you're just looking for a way to load Firefox and Rhythmbox when you log into GNOME, gnome-session-properties is what you want. :wink:

---

### Post by blastus on 2005-09-01
[QUOTE=cayamara]Here's a nice HOWTO on [Making Scripts run on boot time](http://www.debian-administration.org/articles/28). Its for Debian, but should work fine in Ubuntu, since Ubuntu and Debian both use the system V init scheme.[/QUOTE]

Correct me if I'm wrong, but I don't believe you can load X applications on startup with runlevel scripts. These scripts and the run level directories are ONLY used for starting and stopping services at the different runlevels. Also, Ubuntu uses X.Org while Debian still uses XFree86, so some X configuration stuff is different.

I don't know how to run X applications upon logon with GNOME, but with KDE you just create a script in ~/.kde/Autostart, give it execute permissions, and it works for your logon.

---

