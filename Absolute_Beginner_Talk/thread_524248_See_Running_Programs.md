---
title: "See Running Programs?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by lsweet on 2007-08-12
Is there a way to show a list of any programs running in the background?  Similar to task manager in Win?

---

### Post by nonewmsgs on 2007-08-12
> **lsweet said:**
> Is there a way to show a list of any programs running in the background?  Similar to task manager in Win?

yes - administration - system moniter is a lot like it.

---

### Post by lwinkenb on 2007-08-12
I don't know of any GUI programs, but you can always run
```
ps aux
``` from the command line to list all running processes (as well as view memory usage, cpu usage among other things).

---

### Post by yorkie on 2007-08-12
clck on top or bottom panel choose add to panel look for SYSTEM MONITOR highlight icon 
click add

---

### Post by asmoore82 on 2007-08-12
open a terminal and

```
~ $ ps -A
```

to see all processes

```
~ $ top
```
for an interactive view top=?table of processes?
hit 'spacebar' to update and 'q' to quit and '?' or 'h' for help menu.

---

### Post by ramjet_1953 on 2007-08-12
If you right-click on a blank section of  either your top , or bottom task bars, a drop-down menu will open.

Click on[COLOR="Blue"] Add to Panel[/COLOR]

A window will open.  Scroll down to [COLOR="Blue"]System and Hardware[/COLOR].

Select [COLOR="Blue"]System Monito[/COLOR]r. Click on the [COLOR="Blue"]Add[/COLOR] button.

The System Monitor Icon will now appear in your taskbar.

Right-click on the icon and then select [COLOR="Blue"]Open System Monitor[/COLOR].

Click on the [COLOR="Blue"]Processes[/COLOR] tab and you will get a list of every running process.

Reagrds,
Roger :cool:

---

### Post by aysiu on 2007-08-12
Alt-F2 ```
gnome-system-monitor
```

---

