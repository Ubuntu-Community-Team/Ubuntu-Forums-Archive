---
title: "shutdown from terminal"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-04-04
can ne one giv me the command for shutting down from terminal.

---

### Post by rmjokers on 2006-04-04
Try:

sudo halt

or 

sudo shutdown -h now

---

### Post by Randomskk on 2006-04-04
try:
```
sudo shutdown now
``` for a slightly safer shutdown.

---

### Post by mcduck on 2006-04-04
[QUOTE=Randomskk]try:
```
sudo shutdown now
``` for a slightly safer shutdown.[/QUOTE]
without -h the machine won't power off after shutdown.. you'll still need to run 'halt' after that to actually power off the system.

I always use 'sudo halt' or 'sudo reboot' :)

---

### Post by Randomskk on 2006-04-04
ah, ok.. I usually use the graphical shutdown on my desktop, and well my server only gets rebooted :P

---

### Post by tappad on 2006-04-04
[QUOTE=mcduck]without -h the machine won't power off after shutdown.. you'll still need to run 'halt' after that to actually power off the system.

I always use 'sudo halt' or 'sudo reboot' :)[/QUOTE]

I use 'sudo shutdown -h now' all the time and it shuts down properly..
Why would you ned to run 'halt'?

---

### Post by ncappel1 on 2006-04-04
what is the difference if the computer "powers off" after shutting down? If I shut down from the command line, i always just use "sudo shutdown now"

am I missing something?

---

### Post by psquared89 on 2006-04-04
It comes from older computers, if you think back to Win95 / early 98 you would click "Shut Down", and then you'd have to wait.  Eventually, the screen would display "It is now safe to shut off your computer."  At which point you'd have to hit the power button manually.  Nowadays, thanks to the magic of ACPI, a computer is capable of really shutting itself off.

The command   sudo shutdown -h "now"   is gentler than simply "halt", or if you'd like the command sudo poweroff is a synonym that does the same thing.  The little differences are in how long it wait for processes to end (ie telling openoffice to save/close, instead of simply terminating it).  If you'd like to know a little more, open a terminal and type man shutdown.

---

### Post by mcduck on 2006-04-05
[QUOTE=tappad]I use 'sudo shutdown -h now' all the time and it shuts down properly..
Why would you ned to run 'halt'?[/QUOTE]
with the -h, you don't, because 'shutdown' will call 'halt' after it has finished.

I use 'halt' because it's faster to type than 'shutdown -h now', and it will call 'shutdown' to do the shutdown process before halting the system ;)

---

### Post by dcstar on 2006-04-05
[QUOTE=mcduck]with the -h, you don't, because 'shutdown' will call 'halt' after it has finished.

I use 'halt' because it's faster to type than 'shutdown -h now', and it will call 'shutdown' to do the shutdown process before halting the system ;)[/QUOTE]
I find
```
init 0
```
most effective (and easy to type....)

---

