---
title: "installed X11, is not recognized in failsafe_xterm"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Benjam on 2008-03-06
I'm trying to take care of a bug in my system where my starting Terminal results in my system restarting to the login screen(I'm using Xubuntu).

The formula I found(via another thread) is the following:

In xterm session, type:

cd/etc/X11

Then type:

sudo cp xorg.conf xorg.conf_backup

Then type:

sudo nano xorg.conf

And then adjust a depth setting and then save.


Now, the session that I chose was failsafe_Gnome, which gives a pop up saying that it failed to run and will instead run failsafe_xterm(or just xterm. I don't remember which).

So in that terminal box of xterm I typed cd/etc/X11, and it responds saying there is no such directory.

Before I did that I went into that xterm and installed X11 using:

Sudo apt-get install xserver-xorg

That resulted in X11 being installed under the etc file, but it is not recognized in xterm.

What can I do?

EDIT

Response to jw5801

In xterm:
I typed: cd/etc/X11
response: no such file or directory
I typed: cd etc/X11 (wondering if a space was needed)
response: no such file or directory
I typed: sudo cp xorg.conf xorg.conf_backup
response: password:
I typed password
response: cp: cannot stat 'xorg.conf': no such file or directory
I typed: sudo nano xorg.conf
Response: box changes to GNU nano 2.0.6 File: xorg.conf

the File: xorg.conf was a empty box, with commands at the bottom, to ask for help. to exit, etc. I don't know how to use the box, and end up turning my computer off by hitting the power button.

---

### Post by jw5801 on 2008-03-06
If you were in a graphical environment at all, then X11 was already installed. Can you post exactly what you put into the terminal as well as exactly what came out? ie. copy and paste. xterm is simply a different terminal emulator, an alternative to gnome-terminal which is the Ubuntu default.

---

### Post by oldos2er on 2008-03-06
The command you're looking for is "cd /etc/X11"

 In a terminal, the Tab key is your friend. You could just type "cd /e" then hit Tab, and it will complete the directory name for you.

---

