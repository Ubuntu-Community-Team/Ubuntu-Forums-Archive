---
title: "xorg.conf showing as read-only"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by little brad on 2007-05-06
hello all, first post here. long time windows user, just installed ubuntu today.

running a dual monitor setup, got it working, but now i can't get my terminal to work.

i found a thread saying that adding this code

Section "Extensions"
Option "Composite" "false"
EndSection

to the xorg.conf file would fix the problem, however when i try to edit and save, it says the file is read-only and i cannot save over it.

i am the administrator and only user of the system, and when i view the permissions tab under properties it says that i am not the owner and cannot change the permissions of the file.

any ideas?

TIA.

---

### Post by bobplano on 2007-05-06
did you open it using gksudo gedit /etc/X11/xorg.conf? that will give you root powers with it

---

### Post by taurus on 2007-05-06
You are a user on the system with a root privilege.  To edit anything outside your $HOME directory, you need to use sudo command.

```
gksudo gedit /etc/X11/xorg.conf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Billy McCann on 2007-05-06
xorg.conf belongs to the super user (root).  As your normal user, you don't have editing abilities.  so you need to be granted super user abilities for a moment.  (up up and away!)  

open via a terminal using "sudo" or "gksudo".  (Applications > Accessories > Terminal)

First, backup your existing xorg.conf.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now, open the file with super user permissions.
```
gksudo gedit /etc/X11/xorg.conf
```

Now you can edit it.  Save it.  Restart X for the new configuration to take hold.  (ctrl-alt-backspace)

If it doesn't work, you can restore to your former xorg.conf.
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

It's just that easy!

---

### Post by little brad on 2007-05-06
i can't get into the terminal. that's my whole problem. :(

---

### Post by taurus on 2007-05-06
Boot into recovery mode from GRUB menu and edit your /etc/X11/xorg.conf from a console.

```
nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by aysiu on 2007-05-06
> **little brad said:**
> i can't get into the terminal. that's my whole problem. :(
What happens when you press Control-Alt-F1?

That should give you a fullscreen terminal.

If you want to get back to your graphical area, press Control-Alt-F7.

---

### Post by little brad on 2007-05-06
okay, got into the full screen terminal. tried taurus' code, but it wouldn't let me save. said permission denied.

tried Billy McCann's solution, and it says "Gtk- WARNING cannot open display:" when i typed the "gksudo gedit /etc/X11/xcorg.conf" line.

:(

EDIT: i was too quick to read taurus' response where he said to boot into the recovery mode to change it.

all is well. thanks so much!

---

### Post by Billy McCann on 2007-05-06
> **little brad said:**
> tried Billy McCann's solution, and it says "Gtk- WARNING cannot open display:" when i typed the "gksudo gedit /etc/X11/xcorg.conf" line.
You got that error because the program "gedit" requires a working xorg.  :KS 

I didn't know you didn't have X.

Glad to hear all is cool though!

---

