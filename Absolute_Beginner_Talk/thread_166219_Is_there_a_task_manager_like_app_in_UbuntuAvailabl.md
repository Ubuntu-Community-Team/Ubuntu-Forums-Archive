---
title: "Is there a task manager like app in Ubuntu/Available?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-04-26
Is there an application like Windows task manager for Linux/in Ubuntu? Or a way to do so via command line (or both)?

---

### Post by gerbman on 2006-04-26
Applications->System Tools->System Monitor

From the command line you can do ```
ps -e
``` to look at all running processes, or ```
top
``` to get CPU and memory usage.```
kill <PID>
``` will kill process <PID> as listed by the "ps" command.

---

### Post by majstor on 2006-04-26
[QUOTE=Just4]Is there an application like Windows task manager for Linux/in Ubuntu? Or a way to do so via command line (or both)?[/QUOTE]

Do this in the terminal

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

then


gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

and will have gnome-system-monitor when pressing ctrl-alt-del

---

### Post by therunnyman on 2006-04-26
An app?  Sure!

My favorite task manager-like apps are GKrellM and Conky.  They're both in the repositories.  Conky's still got a few bugs, but it rocks nonetheless.

You've also got System Monitor in Apps-->System Tools.  It's cool, but maybe not as cool as either GKrellM or Conky.

---

### Post by syxbit on 2006-06-10
i thought you needed to do 
kill -9 <PID>
not
kill <PID>

---

### Post by gavagai on 2006-06-10
[QUOTE=syxbit]i thought you needed to do 
kill -9 <PID>
not
kill <PID>[/QUOTE]

"kill -9" is a bad habit and can cause you problems.  Only use -9 if you know exactly what you are doing and nothing else works.

When you kill a process you want it to "clean up".  kill -9 does not let it clean up.

---

### Post by syxbit on 2006-06-10
for some reason just doing 
kill <PID>
doesn't do anything.
when ii list with 
ps
it shows (for example
7324 pts/0    00:00:00 elinks
i do
kill 7324
but when i run 
ps
again, it's still there
only by doing 
kill -9 7324
do it go away (from ps)
could someone explain

---

