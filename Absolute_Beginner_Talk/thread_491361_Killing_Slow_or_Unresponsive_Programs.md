---
title: "Killing Slow or Unresponsive Programs"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Caedis on 2007-07-03
Linux is just plain amazing, so stable, so reliable... but occasionally I will get an app that just is so incredibly slow to start or slows to a crawl and wont respond for a long time to any input.
The question is, how do I kill a running process. I am aware that the "X" button at the top of the window does do a good job at killing them, but I have had several situations where the force quit dialog is covered up by the unresponsive program.

In windows I press [Ctrl] + [Alt] + [Del]  and go to the process in task manager and end the process that way.... How do I get that same outcome in Linux?

---

### Post by rodo-&gt;dave on 2007-07-03
one way:
on the cli: ps -eaf|grep really_slow_program
this will give you a 'pid'
on the cli: kill pid

---

### Post by Caedis on 2007-07-03
Is there a keystroke for this or a portion of this?

---

### Post by Nekiruhs on 2007-07-03
Or, the easier way:
```
killall <name of unresponsive program>
```
or ```
xkill
```

---

### Post by sab0403 on 2007-07-03
Something better - a panel app.

Right-click on an open portion of either panel (top works better because it's less crowded) and click on "add to panel". Then go to "Desktop and windows" and double click on the "Force quit" app.

That should work for you. :popcorn:

---

### Post by jml on 2007-07-03
If you know the name of the process you want to stop, and there is only one process with that name another option from the command line is:

$ killall "name of process"  

If the process does not terminate within a few seconds add the -KILL argument:

$ killall -KILL "name of process"

This saves you the trouble of looking up the PID.

Joe

---

### Post by rodo-&gt;dave on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=490795](http://ubuntuforums.org/showthread.php?t=490795)

---

### Post by notwen on 2007-07-03
System--->Administration--->System Monitor

From here you can kill any process simply by highlighting said process and clickign the "Kill" button.  You could also open up a terminal and type
```
ps ux
```

From this list locate the application that is slow or not responding and kill it's PID(process id) using this command

```
kill XXXXX
```

XXXXX being the application process id from the "ps ux" command.  Hope this helps and good luck. =]

---

### Post by Caedis on 2007-07-03
All great options!  Ill definatly use the CLI approach when jacking around in BASH... But I like the nice elegant approach of the force quit panel app when in GUI.  Good stuff, 

thanks!:p

---

### Post by Niniel on 2007-10-16
That is all nice and dandy, but how do you deal with a crashed full screen app? Of course <ctrl> <alt> <backspace> will always work, but I'd like to be able to get back to the desktop without having to log back in.

---

### Post by akiratheoni on 2007-10-16
> **Niniel said:**
> That is all nice and dandy, but how do you deal with a crashed full screen app? Of course <ctrl> <alt> <backspace> will always work, but I'd like to be able to get back to the desktop without having to log back in.

When OpenArena would crash on me, I would hit Ctrl+Alt+F2 (or F1, F3, F4, etc.)

It would get you to a terminal... then you do the method that the above users mentioned.

Personally, I would do a ps -e 

then find the process' ID I needed to kill, then type in

kill [pid]

But the killall [process name] might be faster.

Afterwards, hit CTRL+Alt+F7, then you're back to your desktop.

---

### Post by strabes on 2007-10-16
By the way, if you don't know the exact process name, you can use tab completion to figure it out. Firefox is really the only program that ever crashes on me, so in a terminal I type "killall fir" then hit <tab> and it completes it to "firefox-bin" for me.

I also have a keyboard shortcut (win+x) to "xkill" If you don't know how to set keyboard shortcuts to custom commands, check [here](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/).

---

### Post by Niniel on 2007-10-16
Cool.

Is there a switch for PS that makes it show just one screen of programs at a time? Kind of like DOS's "dir /p"?

---

### Post by adamorjames on 2007-10-16
I really like killall combined with tab completion it is awesome. For instance if you don't know the name of what you want to kill, you can type "killall " and then press tab and it will give you a list of all processes running and then you just find the one you want and put it in and viola. :)

---

