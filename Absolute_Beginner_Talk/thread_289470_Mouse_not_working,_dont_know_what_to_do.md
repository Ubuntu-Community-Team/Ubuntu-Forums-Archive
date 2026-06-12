---
title: "Mouse not working, dont know what to do"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by leopard6661 on 2006-10-31
I read in the forum that serial mouse is not detected in xubuntu, I just finished unstallation and I have the same problem, I tried using Alt+F2,(as mentioned in the thread) the run window opened but when I typed #sudo vi /etc/X11/xorg.conf all I get was a run error saying :the command failed to run, text was empty (or contained only whitespace) I tried writing the command from xterm, but got the messege command not found.
I am a complete nupe to Linux and xubuntu, I was hoping any one can help
please, without the mouse I cant use the computer at all
thanx in advance

---

### Post by hopstah on 2006-10-31
if you are doing something from the run menu instead of the terminal, you need to use a graphical super user prompt.  for gnome, try ```
gksu vi /etc/X11/xorg.conf
```and for kde use ```
kdesu vi /etc/X11/xorg.conf
```this will bring up a window which prompts you for a password.  if you are executing commands from a terminal, it doesn't matter which one you use, sudo and gksu or kdesu will all do the same thing.

---

### Post by leopard6661 on 2006-10-31
Thanx for ur fast reply
I did what u said, but after having the password window, I typed my password, and loading..........then nothing at all

---

### Post by Shinoda on 2007-11-03
> **leopard6661 said:**
> I tried using Alt+F2,(as mentioned in the thread) the run window opened but when I typed #sudo vi /etc/X11/xorg.conf all I get was a run error saying :the command failed to run, text was empty (or contained only whitespace)
Should've been
```
gksudo mousepad /etc/X11/xorg.conf
```
Alternatively run [FONT=Courier New]xfce4-terminal[/FONT] to open up a terminal.

---

