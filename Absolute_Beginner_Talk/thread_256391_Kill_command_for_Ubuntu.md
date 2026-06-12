---
title: "Kill command for Ubuntu"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-09-12
If you have an application hanging is there a kill command for Ubuntu?

---

### Post by jordanmthomas on 2006-09-12
yes...it is kill  :)
for example...in a terminal say you want to kill firefox
you would find its Process ID (pid) by doing this
```

ps -A | grep firefox

```
this lists all processes and then searches for firefox

You will get something like this:
```

jordan@jordan:~$ ps -A | grep opera
19306 ?        00:00:44 opera
19509 ?        00:00:02 operapluginwrap
19510 ?        00:00:00 operapluginclean

```
Say I wanted to kill opera (and its plugins)
I would type 
```
kill {19306, 19509, 19510}
```
This would kill each of the processes I want dead.

If you know the name of the executable (firefox, for example has *firefox* and* firefox-bin*
you could do this
```
killall firefox firefox-bin
```

My favorite way (because of the skull and crossbones) is to run xkill (but it will only work on X applications..)



**edit**

to kill just one process, you don't really need the curly braces
```
 kill 1234
```
would work just fine.

---

### Post by bodhi.zazen on 2006-09-12
```
killall name_of_command
```

If that does not work, see above.

---

### Post by icksa on 2006-09-12
Hi:
If it is a graphical application, you could also type xkill in a terminal. Then you just click on a window to want to close.

You can also add the force quit applet to your panel on the desktop.

---

### Post by Burke on 2006-09-13
Yeah, all the above is correct, but if you *really* want to kill a process NOW, use:

```
killall -9 firefox firefox-bin
```

...or obviously substitute anything in for the appname(s).

---

### Post by Arevos on 2006-09-13
You can also kill processes through the System Monitor (System -> Administration -> System Monitor). Automatix gives you the option of hotkeying the System Monitor to Ctrl-Alt-Del, which I find rather useful.

---

### Post by jmtjet on 2006-09-13
Thanks to all. I've got all of your replies in my notes. :)

---

### Post by Circus-Killer on 2006-09-13
a much simpler way (if its a windowed app), is to open a terminal and execute the following:
$ xkill

then just click on the app you wanna kill.

---

### Post by KD6TZF on 2008-02-01
> **Arevos said:**
> You can also kill processes through the System Monitor (System -> Administration -> System Monitor). Automatix gives you the option of hotkeying the System Monitor to Ctrl-Alt-Del, which I find rather useful.

I tried to use the Synaptic Package Manager to locate _Automatix_ but had no luck.  I looked around the System Monitor, but didn't see any mention of _Automatix_ either.  How do you get that key combo tied to that process?  I have occasionally wanted to kill the process without rebooting.  It seems recently (since updating to Gutsy) that Firefox seems to hang more frequently, especially when a script is running.  What is the fix?

Thanks,

---

### Post by hyper_ch on 2008-02-01
Automatix is not recommended!

You can edit your keyboard layout and I think there's already a default action for killing an application there... you just need to assign it a key-combo...

If not create a new one with xkill and apply a key-combo to that.

---

### Post by KD6TZF on 2008-02-01
> **hyper_ch said:**
> Automatix is not recommended!

You can edit your keyboard layout and I think there's already a default action for killing an application there... you just need to assign it a key-combo...

If not create a new one with xkill and apply a key-combo to that.

I just ran it, but didn't see any way to assign a key-combo?  Sometimes when I close, or try to close Firefox, the window closes, or appears to close.  Then when I try to restart it, I get an error message saying it is already running???  I'd like to really kill it, know it's dead, and restart it without rebooting.

Thanks,

---

