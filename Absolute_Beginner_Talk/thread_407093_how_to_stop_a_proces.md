---
title: "how to stop a proces"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-11
My Firefox just shut's down sometimes, and when I try to reopen it says that one proces is alredy running. How to terminate proces manualy? Is there something like CRTL+ALT+DEL on windows?

---

### Post by igknighted on 2007-04-11
System->Admin->System Monitor is a close equivelent, but I usually open a terminal and use the command "killall <processname>".  Either that or run "top", then hit 'k'.  It will ask what process ID to kill, so type the number next to the crashing process and hit enter to kill it.  Some apps/processes you might need to be root to kill.

---

### Post by ComplexNumber on 2007-04-11
> **cele said:**
> My Firefox just shut's down sometimes, and when I try to reopen it says that one proces is alredy running. How to terminate proces manualy? Is there something like CRTL+ALT+DEL on windows?
i always have the system monitor applet on my panel. go to your panel and right click on it. then select 'add to panel'. select the system monitor. 
to open it up, just click once on it with your left mouse button. you will see a list of processes in the Processes tab. click once on the process name to order the name of the process alphabetically, then click on it again to reverse the order. that should help you to find the process. once youve found it, jsut right click on it and choose to 'kill process'.

---

### Post by allforcarrie on 2007-04-12
after a swiffox freeze i get a process listed as uninteruptable, the only way i can kill it is to reboot.

---

### Post by pirothezero on 2007-04-12
type in ps aux | grep nameofprogram look up the pid and then do sudo kill -9 pid#.

---

