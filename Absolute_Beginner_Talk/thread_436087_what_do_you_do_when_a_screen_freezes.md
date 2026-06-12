---
title: "what do you do when a screen freezes?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-07
When using ubunto to look around at NTFS files in my XP partition the window freezes.

Can this happen?

And if so is there a way to stop it or escape the problem?

Is there a neet litle trick like in windows where you do the vulcan death grip of pressing control,alt and delete?

Cheers

---

### Post by fakie_flip on 2007-05-07
try pushing all of these at the same time when it happens control alt backspace

---

### Post by LuisGMarine on 2007-05-07
Well if the whole window freezes, as in your entire desktop, like the user said above, hit all of these buttons together:

ctrl + alt + backspace.

If just a single window freezes, lets say firefox.  Open up terminal or hit alt + F2, and type in this command:
```
xkill
```
This will turn your cursor into an x, use it to click on the program that is freezing, this will instantly kill the application.

Good Luck

---

### Post by DarthWHO on 2007-05-07
BTW, ctrl+alt+backspace will end your current session. Effectively closing any unsaved documents. Do this with caution... (responded at the same time as LuisGMarine above)

If you have access to your other functions and it's just the current Nautilus window that is frozen, you can kill the process by using System Monitor (just one way if you are a Windows Task Manager kind of guy)

Didn't know about xkill, very cool!! Still a newb myself ;)

---

### Post by mcduck on 2007-05-07
'killall' will stop programs by name, for example 'killall firefox' stops Firefox.
'xkill' works usually, but in some cases it only kills the use interface, leaving the program itself still running.

Just clicking on the window's 'close' button a couple of times usually also opens a dialog asking if you want to force quit the program. Right-click and 'close' from the task bar does the same thing.

Of course the System Monitor can be used too, and it's possible to bind it to Ctrl-Alt-Del shortcut, if you are used to doing that a lot in Windows ;)

Ctrl-Alt-Backspace is the last way, if everything else fails. This will restart the whole X session and throw you back to login screen.

edit: if your system is so badly frozen that even Ctrl-Alt-Backspace doesn't help, you could try following: hold down Alt+SysRq and type r-e-i-s-u-b to make a clean reboot, syncing your drives properly etc. than just hitting the power button would do. Alt-SysRq-r switches raw keyboard mode off, Alt-Sysrq-e ends all programs, i kills everything that didn't end properly, s syncs all drives to minimize data loss, u remounts all drives as read-only and finally b reboots the machine. This should work as long as the kernel itself is running.

---

### Post by fakie_flip on 2007-05-07
pkill nautilus
killall nautilus
kill `pidof nautilus`
xkill

There are lots of ways. If those don't work use -9 after them for example.

pkill -9 nautilus

---

### Post by fakie_flip on 2007-05-07
> **mcduck said:**
> 'killall' will stop programs by name, for example 'killall firefox' stops Firefox.
'xkill' works usually, but in some cases it only kills the use interface, leaving the program itself still running.


Actually killall firefox will not work because the process name is firefox-bin, so you have to type.

killall firefox-bin

However this will work because it searches for any process with firefox in the name.

pkill firefox

---

### Post by hessiess on 2007-05-07
that's better than windows! i quite often just haft to hit the power button:lolflag:

---

### Post by Nythain on 2007-05-07
i love learning... all this time i never really knew about pkill and xkill... sweet

---

### Post by mcduck on 2007-05-07
> **fakie_flip said:**
> Actually killall firefox will not work because the process name is firefox-bin, so you have to type.

killall firefox-bin

However this will work because it searches for any process with firefox in the name.

pkill firefox

yeah, that's true. I've never actually had to kill Firefox so I didn't even remember that it's executable is firefox-bin.. I just pulled some example out of hat :D

pkill is a new one for me. But sounds like you really have to be careful with that one, so you won't actually kill more stuff than you meant to.

---

### Post by fakie_flip on 2007-05-07
> **mcduck said:**
> yeah, that's true. I've never actually had to kill Firefox so I didn't even remember that it's executable is firefox-bin.. I just pulled some example out of hat :D

pkill is a new one for me. But sounds like you really have to be careful with that one, so you won't actually kill more stuff than you meant to.

yes, you do have to be careful with pkill, but pkill can't kill any important processes unless you run it with sudo. then it can kill processes started by root. here's an example from my computer.

chris@ubuntu:~$ pkill init
pkill: 1 - Operation not permitted
chris@ubuntu:~$ pkill syslogd
pkill: 4944 - Operation not permitted
chris@ubuntu:~$ pkill xinetd 
pkill: 5324 - Operation not permitted
chris@ubuntu:~$ 

but use those commands with sudo, and you will be in trouble. it will crash your system, and you'll end up rebooting.

---

### Post by LuisGMarine on 2007-05-08
With all these weapons at your fingertips to terminate a program, I think programs will now think twice before the decide to freeze up on you :)

Hope you learn something, I sure did :)

---

### Post by jiminycricket on 2007-05-08
What video driver are you using?  nVidia or ATI binary blob dribers?

---

### Post by fakie_flip on 2007-05-08
kill -STOP $(pidof gnome-panel)

Now click on Applications in your Gnome panel. Next do this one.

kill -CONT `pidof gnome-panel`

---

