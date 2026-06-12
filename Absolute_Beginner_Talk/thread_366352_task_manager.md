---
title: "task manager"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-20
I am new to ubuntu and am used to Windows. I would greatly appreciate if you could tell me the equivilant of ctrl alt del in windows for ubuntu. I mean that I want to know how to get the task manager so that I can force a program to close. I have been having some problems with some programs freezing up so I need to ability to force a program to close. Thank you.

:KS

---

### Post by Zuuswa on 2007-02-20
if it is a graphical application, i.e. you can see the window that is frozen, you can just type in ```
xkill
``` into a terminal, and then left click on the application that is frozen.  If you cant see the program, but now what the process name is, you can type in ```
killall appname
```.

Also, I believe if you go to System>Administration>System Moniter it will give you a graphical application that shows your processes like windows does.

---

### Post by jjf on 2007-02-20
You can also right-click one of your desktop's panels (the bars where menus, etc, are), click "Add to Panel," and add the System Monitor to your panel.  

I like this because it shows the processor load while you're working.  Click on it once to bring up the System Monitor (=Task Manager).

"Force Quit" is another handy little app you can add to your panel.  Click the "Force Quit" icon,  then click a frozen program to shut it down.

Last thing: Download and run Automatix.  It will install a little app that binds CTRL+ALT+DEL to your System Monitor.

---

### Post by mcduck on 2007-02-20
You'll find the System Monitor in System/Administration/System Monitor.

If you want to start it with Ctrl-Alt-Del you can do it this way:

1. Open Configuration Editor (hit Alt-F2 and run gconf-editor).
2. Browse to apps/metacity/keybinding_commands
3. Set the command_1 to gnome-system-monitor.
4. Browse to apps/metacity/global_keybindings
5. Set run_command_1 to <Control><Alt>Delete

(This works only in Gnome desktop with no Compiz or Beryl running. For those, use their own shortcut options)

---

