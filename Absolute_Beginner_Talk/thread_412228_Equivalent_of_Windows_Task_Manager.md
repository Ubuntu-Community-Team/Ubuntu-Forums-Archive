---
title: "Equivalent of Windows Task Manager"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-04-17
What is the Linux equivalent of the Windows Task Manager?  In Windows when you press Ctrl+Alt+Del you get a nice, pretty Task Manager window popping up.  I'm looking for something similar, or at least something I can use to kill a running process.  Thanks in advance for the help.

---

### Post by Skidpad on 2007-04-17
You can open a terminal and enter the command **top** to see the currently running processes, sorted from high-to-low.

If you install Conky, you can display the top processes at all times.   (Conky is a desktop applet that can display many different things - check the "Post Your Desktop" sticky in the Cafe for many screenshot examples of what it can do).

---

### Post by Thrasonic on 2007-04-17
Cool.  Thanks for the help.

---

### Post by N Clement on 2007-04-17
I actually got a ctl-alt-dlt replacement that brings up the system monitor when I push those keys, but now I can't remember where I got it #-o.  Maybe system monitor is what does it?

---

### Post by zekopeko on 2007-04-17
^^^
i think it's from automatix2.

---

### Post by N Clement on 2007-04-17
It is indeed.  Look in Automatix2 under Misc. if you would like to get that configured.

---

### Post by noerrorsfound on 2007-04-17
System > Administration > System Monitor

---

### Post by josephus on 2007-04-17
just add a keybinding that loads up the system monitor when you hit control+alt+delete

where you add your keybindings sometimes depends on which window manager you are using, but if you are using metacity just go to system->preferences->keyboard shortcuts

add a custom keybinding for ctrl+alt+delete that will launch gnome-system-monitor

---

### Post by maki_03 on 2007-05-29
if you want the gnome-system-monitor to pop-up when you press ctrl-alt-del like the task manager, you could check out this site:
[http://technowizah.com/2006/11/debian-how-to-task-manager-xp-style_02.html](http://technowizah.com/2006/11/debian-how-to-task-manager-xp-style_02.html)

hope it helps! :D

---

### Post by zeddock on 2007-06-29
> **maki_03 said:**
> if you want the gnome-system-monitor to pop-up when you press ctrl-alt-del like the task manager, you could check out this site:
[http://technowizah.com/2006/11/debian-how-to-task-manager-xp-style_02.html](http://technowizah.com/2006/11/debian-how-to-task-manager-xp-style_02.html)

hope it helps! :D


Helped me!
Thought the Metacity worked before then when I saw the post at the above link, realized it just stopped because I started using Compiz.

Thanx!

zeddock

---

### Post by hyper_ch on 2007-06-29
if you want terminal output (like "top") but a bit more fancy then install "htop" :)

---

