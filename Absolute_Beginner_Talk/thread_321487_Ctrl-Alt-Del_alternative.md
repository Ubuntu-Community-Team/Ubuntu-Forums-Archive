---
title: "Ctrl-Alt-Del alternative"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-19
I am running Ubuntu on a 128 MB RAM, pentium II processor. It is working fine infact better than Windows. Sometimes when I run multiple programs it goes into an hang state and recovers only after a while. Sometimes some programs simply crash. Is there a way I can monitor programs that are running and force them to terminate as per my wish. Something like Ctrl-Alt-Del in windows.

---

### Post by deadgobby on 2006-12-19
This one is soo cool. Atl+f2 and type in xkill. It will bring up the old cross bones as your mouse pointer and click on the program. It Kills it like a roach.
Gobby
PS if you can pump up the ram

---

### Post by vivin_west on 2006-12-19
Ha ha. This one is cool. I will use it. But no not like this. I want to see all the programs that are running first. Even the ones that are not  visible on the screen. Say I run evolution and then want to terminate it immediately. Evoltuion will not be visible on the screen. Then what to do.

---

### Post by deadgobby on 2006-12-19
Oh Crap. I know this one and it is on the tip on my head. ](*,)

---

### Post by aysiu on 2006-12-19
In Kubuntu, the keyboard shortcut is Control-Escape. There is no predefined keyboard shortcut in Gnome, as far as I know, but you can **[create a keyboard shortcut for it](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)**, and the command you're looking for is *gnome-system-monitor*.  It brings up a nice little window like this.

By the way, on 128 MB of RAM, I wouldn't be running Ubuntu--Xubuntu would be a better choice, or even **[IceWM](http://ubuntuforums.org/showthread.php?t=263710)** or Fluxbox.

---

### Post by macogw on 2006-12-19
Hey, deadgobby, I just went "oh really? neat!" and tried it and clicked on a minimized Window.  Gnome panels were killed instead.  Warning to everyone: it doesn't work on minimized stuff!  Um, aside from that, my battery/power monitory thingy is no longer part of the panel.  It's all floaty in its own box.  Any idea how to put it back? (No, "Add to Panel" does not add the same little applet)

---

### Post by 3rdalbum on 2006-12-19
If there's a program that's hung, and you want to kill it, you can add the "Force Quit" applet to one of your Gnome panels. It does the same thing as Xkill, except it looks more professional.

---

### Post by tkjacobsen on 2006-12-19
go to the console "ctrl + alt + f1"

log in.

use "top" to see the programs using most resources.
use "ps -A" to see all running processes (Note the process id (PID)"
use "ps -A | grep processname" to see the process id of som specific process

use "kill PID" to kill the process with process id PID

alternatively use
"killall processname" where processname is eg. firefox-bin or gedit (the name shown in top or ps -A)

---

### Post by ]Nbx*cmD[ on 2006-12-19
Much more effective:

1 · Ctrl+Alt+F1 -> will take you to a tty
2 · Log in
3 · type ps -A | more
4 · remember the PID of the process you want to kill
5 · type kill -9 [process_pid]

and that's it!

---

### Post by ]Nbx*cmD[ on 2006-12-19
oh sorry tkjacobsen already answered right while i was writing my post x'DD
Well, we both forgot to explain how to come back to graphical mode, which is done by pressing Alt+F7

---

### Post by maxamillion on 2006-12-19
> sudo aptitude install htop
htop

give that a try ... great utility and more user readable than top for beginners and pros alike.

---

### Post by lmo on 2007-01-03
System Monitor

Program name is gnome-system-monitor

---

