---
title: "Killing a running app"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by canuck45 on 2005-11-25
Ok, this will sound strange but I am sure linux users have come across this before.

I was running TVtime to watch TV while on the net,  I was playing with interlacing, blah blah blah and suddenly the screen disappeared.  I am still hearing the show being broadcast but cannot see it.  It is not minimized anywhere, if I relaunch the program it pops up for a second then disappears again.

I tried ps -A and saw nothing that seems to be my program.  This happened once before with a audio program.  What can I do besides reboot.  How do I find running apts that hide themselves....at least it hasn't brought down my whole system....

HELP I can't change channels and Oprah is on...aaaaggggg

---

### Post by teaker1s on 2005-11-25
install gnome-system-monitor if you like a windows type task manager
or in konsole type xkill and use the mouse to kill the app

---

### Post by super on 2005-11-25
type [FONT="Courier New"]top[/FONT] in a console window. it will list all running applications and processess.
to kill a running application just press [FONT="Courier New"]k[/FONT] in top.

or type [FONT="Courier New"]killall 'programname'[/FONT] in a console window

---

### Post by canuck45 on 2005-11-25
I tried system monitor first and don't see anything related to TVTime running.  Everything listed is sleeping....

ooops now system monitor is not responding to anything....and has gone blank all white.

and my panel is covered by partial windows...

panel not working, desktop terminal shortcut launches a terminal window all black instead of white, accepts no input from keyboard....must force quit cannot raise elephants!

only apps on desktop launching and not properly....

---

### Post by super on 2005-11-26
i know this is a late reply, but in the future pressing alt+ctrl+backspace will kill the X server completely (along with all X applications) and prompt you to log in again.

---

### Post by cwaldbieser on 2005-11-26
[QUOTE=canuck45]I tried system monitor first and don't see anything related to TVTime running.  Everything listed is sleeping....

ooops now system monitor is not responding to anything....and has gone blank all white.

and my panel is covered by partial windows...

panel not working, desktop terminal shortcut launches a terminal window all black instead of white, accepts no input from keyboard....must force quit cannot raise elephants!

only apps on desktop launching and not properly....[/QUOTE]

Pressing CTRL+ALT+F1 will take you to a virtual terminal where you can log into a command line where you can run some of the commands others have mentioned.  It is useful to do that if some X app goes crazy and hides the desktop from you.

Pressing CTRL+ALT+F7 should take you back to X once you rectify the situation.

---

