---
title: "newbees' blowin it"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by retro on 2005-12-11
Can't figure out how to log in as root. Also can't get out of GUI and into text screen.

---

### Post by dcast on 2005-12-11
you shouldnt need to log in as root. For that you use the sudo command eg:
sudo synaptic

that would give you root access to the synaptic package manager it will prompt you for a password and just use your user password

---

### Post by aysiu on 2005-12-11
[QUOTE=retro]Can't figure out how to log in as root.[/quote] You shouldn't have to. Say what you're trying to accomplish, and I'll tell you how to do it without enabling a root login. For more info, see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) 

> Also can't get out of GUI and into text screen. You don't have to get out of GUI to enter commands. Go to Applications > Accessories > Terminal

If you really want to get out of the GUI, though, hit control-alt-F1

---

### Post by hod139 on 2005-12-11
See [this wiki page]("https://wiki.ubuntu.com/RootSudo?highlight=%28root%29") about the root user.

What do you mean "Also can't get out of GUI and into text screen".  
You can always go to a virtual terminal by pressing "Ctrl-Alt-F1"
Or you can launch a console from the menu.  Maybe you can be more specific if this doesn't answer your questions.

Never mind, people beat me too it :)

---

### Post by DiscoKiller on 2005-12-11
by text screen do you mean terminal? if so just run a terminal shell in the GUI. or from the GRUB loader you can run ubuntu without X.

---

### Post by deNoobius on 2005-12-11
The text screen is at Applications--Accessories--Terminal.

Generally, Ubuntu is structured with the idea that you wouldn't be logging in as root.  Most commands that require root access are accomplished by adding "sudo" (or gksudo if you're using the Gnome desktop GUI, for example, if you're setting up a launcher for a program that requires sudo) before the command.  There are instructions to be found here for logging in as root if you really have to.  Also, Automatix, also found online here (just do a search) can add a little script that lets you run an item as root by right-clicking and making a selection.

---

### Post by aysiu on 2005-12-11
If you think you need to log in as root, what you most likely need to do is Alt-F2 and type ```
gksudo nautilus
```

---

### Post by az on 2005-12-11
Boot into recovery mode and you are root *and* in text mode.  You have to press escape to reveal the grub menu when you boot, if it is not already displayed.

There is no root account in Ubuntu.  You can create one if you wantm but it is pointless.  Ubuntu uses sudo for privilege escalation.

See the soduroot wiki page

wiki.ubuntu.com/UserDocumentation

(edit - I type slow)

---

### Post by retro on 2005-12-11
Many thanks; Stuck on stupid recalling previous attempts to use Linux. "Login: root" and all that. Amazing response to my bleat.

My head is slowly coming to a point.

Cordially, Glenn

---

