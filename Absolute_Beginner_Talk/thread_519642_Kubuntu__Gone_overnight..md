---
title: "Kubuntu  Gone overnight."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by owenb@theofficenet.com on 2007-08-07
Last night I left my Kubuntu box on downloading some updates.  This morning I noticed that my keyboard was not responding so I rebooted. Everything seemingly started o.k. I got the Kubuntu splash screen in color. Then things changed.
The following is what I ended up with on a black screen.

" Starting up...
Ubuntu 6.10 owen-desktop tty1
owen-desktop login:
Password:"

  after giving my login name and password the screen continued with:
"Last login: Tue Aug 9.01:1349 2007 on tty1
Linux owen-desktop 2.617 generic #2 SMP"

   This was followed by some general legal type information. The last line on the screen read:
owen@owen-desktop:~$

owen-desktop is the name of the computer.

Is there anyway to regain my installation.  I have a very slow dialup account and would hate to have to reinstall with all the updates.
Owen

---

### Post by Inxsible on 2007-08-07
Try typing 

```
startx
```at the prompt

---

### Post by asmoore82 on 2007-08-07
your system is still working ... just without the GUI (Graphical User Interface), the X11 Windowing System

rebooting and choosing your older kernel from the GRUB list should get you back to something a little more managable ... my guess is that you had a specialty graphics driver installed for the older kernel that didn't carry over to the new kernel ...

If the system really was hard-locked as you say it would have to be some type of hardware issue.
But if it happens again here are the procedures for safely getting the system down ...

1. Ctrl+Alt+Backspace = "Zap" the X11 Session - kills the graphics and they should restart.
if that doesn't work ...
2. Ctrl+Alt+F1 = drop down to the text terminal you are at now, then ctrl+alt+del to reboot.
if that doesn't work ...
3. hold SysRec (near printscreen) and hold Alt, then slowly press and release in order: E, S and O =
Emergency term, Sync data, and power Off. if this doesn't work you have a true system lock up
and in my experience, this *Never* happens in linux unless there was a hardware failure.

---

### Post by owenb@theofficenet.com on 2007-08-08
> **Inxsible said:**
> Try typing 

```
startx
```at the prompt
Thanks for responding. It's really appreciated.

The  "startx" command did bring up what I think is a blank Ubuntu screen devoid of any menues. A 'Alt-F2 did bring up a menue for inserting another command.  By any wonderful chance could this be used to reactivate KDE?

I havn't been able to try the other suggestion by asmore82 because my mouse and keyboard are USB hardware and are not fully functionable.  Keys such as the ALT or F keys do not respond. If nothing else works I will substitue PS/2 items.

---

