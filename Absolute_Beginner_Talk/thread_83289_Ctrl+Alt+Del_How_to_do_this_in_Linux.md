---
title: "Ctrl+Alt+Del? How to do this in Linux?"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-10-28
I had a program hang up on me and couldnt figure out how to end it. In windows its Ctrl+Alt+Del.  But it appears this isnt the case in linux. How is this done in linux?

---

### Post by Robgould on 2005-10-28
ctrl-alt-backspace will get you out of X.  Almost like DOS now.  to go back to X, type startx.  This can help if your freeze was something in X or gnome.
 
also under gnome you can go to system tools -> systme monitor (I think...going off memory as I am at work).  You can force processes to stop there.
 
Hope this helps

---

### Post by rmjokers on 2005-10-28
You can run Applications->System Tools->System Monitor.  Not sure if there is a keyboard shortcut for this.  Or, from the terminal, you can do:

  ps aux

and then 

  kill -9 PID

where PID is the process ID from the second column.

---

### Post by wombat20 on 2005-10-28
From memory...

Open a terminal and type: sudo top

This should show a list of the biggest processes.  If you press K then type the process ID (PID) of the process you want to force to quit it will kill it.  Of course you'll lose all unsaved work, blah blah blah...

I think you can also do a :

sudo killall application-name

Perhaps typing: man kill

would give you more info.  Sorry, I'm on an XP machine at work so can't check this for you, atm.  :-/

---

### Post by chrisblack on 2005-10-28
you can add a "kill" applet to the tool bar if you right click on the toolbar... add applet.... scroll down to kill

Chris

---

### Post by drummer on 2005-10-28
"alt-F2" and run xkill, then the next window you click on with the now cross-hair pointer will be killed.

---

### Post by stoeptegel on 2005-10-28
[QUOTE=drummer]"alt-F2" and run xkill, then the next window you click on with the now cross-hair pointer will be killed.[/QUOTE]

Alternatively: crtl+alt+escape and klik the(open!) window

---

### Post by Robgould on 2005-10-28
You could serch this forum for "automatix".  It is a script written to install stuff easily on your computer.  One of the options is to make ctrl-alt-del work like windows.  I have never tried it though.

---

### Post by nitricacid on 2005-10-28
I think the easist way is to either make a shortcut or place the 'Kill'\'System Monitor' on the menu bar. the only problem i see if it is on the menu bar is if the system locks up. (sarcasticly) yea rite.. how often does linux lock up?!

---

### Post by David Marrs on 2005-10-28
Normally you will be given the option to force an application to close if it stops responding. To do this you simply click the window's "close" button and wait a little while.

Presuming this doesn't work, the second easiest option is probably to open the system monitor from Applications->System Tools and terminate the process from there.

If you can't even do that, the only thing left to force the entire gnome session to terminate by typing ctrl-alt-backspace. That will restart the session and take you back to the ubuntu log-in prompt.

---

### Post by Corvillus on 2005-10-28
Assuming your using GNOME with Metacity as a default WM, if you want a Ctrl-Alt-Del behaviour similar to in Windows, you can actually open Applicatitions -> System Tools -> Configuration Editor, then go to /apps/metacity/global_keybindings and change run_command_x (where x is some unassigned command#) to <Ctrl><Alt>Delete then go to /apps/metacity/keybinding_commands and change command_x to gnome-system-monitor.

---

### Post by Darrin on 2005-10-28
Thanks for the info. So many response I have to try them all out. So many different ways. :)

---

