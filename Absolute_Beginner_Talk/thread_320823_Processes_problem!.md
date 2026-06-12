---
title: "Processes problem!"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-18
hi, I've tried to install the aMSN from the Add/Remove applications, but whenever I try it just remains as if it were loading, but nothing happens. Something similar happened to me with the updates for Ubuntu, it just freezed as if it were loading...
so I have two questions: the first one, do I have to do something to install aMSN with the Synaptic Package Manager? or does anyone knows what do I need to do? 
and the second one, is there a way to see the processes and the actions that Ubuntu is making, somtehing like the task manager (ctrl+alt+supr) in Windows?

---

### Post by Ptero-4 on 2006-12-18
gtop (Gnome) and Ksysguard (WinDE) are what you want to see your processes.

---

### Post by Jorge32 on 2006-12-18
and how do I get to enter there? do I have to run a terminal and put something like sudo gtop or something like that?

---

### Post by jordanmthomas on 2006-12-18
top will allow you to see processes that are running.
You can sort it in different ways, see 
```
man top
``` for the various options

To search for a running process (ie dpkg), you can do this:
```
ps -A | grep dpkg
```
If nothing is returned, dpkg is not running.
If dpkg is running, something like this will be returned:
```
14312 ?        00:00:00 dpkg
```
to stop it (be careful), do this
```
sudo kill 14312
```

A graphical version of top, as Ptero-4 mentioned is gnome-system-monitor.
To kill the update manager, you'll need to run it as root, so press Alt - F2 and type
```
gksu gnome-system-monitor
```
To see *all* processes, go to view -- all processes
Here, you can kill whatever you want (again, be careful)

Is this what you were looking for?

---

