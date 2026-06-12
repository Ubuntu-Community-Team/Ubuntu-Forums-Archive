---
title: "whats the equivalent of CRTL + ALT + DEL?? PLEASE?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-10-04
I have a frozen app..

---

### Post by Mimsy on 2006-10-04
If you're using Gnome, there's a function called "force quit"

Right click on a panel, and one of the many things you get the option of putting on the panel is Force Quit. Lock it to the Panel,  then you can click on it whenever something freezes.

If I was on Ubuntu right now I'd be able to be more detailed, but I hope that helps a bit.

/Mimsy

---

### Post by systemintheglitch on 2006-10-04
Thank you.

---

### Post by tonyr1988 on 2006-10-04
Yes, the Force Quit is amazing - I've used it several times. It kills the apps immediately (unlike Windows, in my experience). Two more things along those lines:

[http://www.ubuntuforums.org/showthread.php?t=41174](http://www.ubuntuforums.org/showthread.php?t=41174) will show you how to make Ctrl+Alt+Del show the GNOME System Monitor. It will show you CPU usage per app (like the Windows Task Manager). Not sure if you're using Kubuntu.

Also - if your desktop freezes and won't do anything...try Ctrl+Alt+Backspace. It should turn your screen black for a second and pop you back to the login screen. It's much faster than a restart, and has always worked for me as a last resort.

---

### Post by jISh on 2006-10-04
If you can't "FORCE QUIT", then try this:

Open a terminal, type in *ps -e |more* and use the enter key to scroll through the list. Find your process name, then use *killall x* where x is the name of the process you want to get rid of.

Failing that, Ctrl+Alt+Backspace will restart your X server and kill any X applications.

---

### Post by aysiu on 2006-10-04
Alt-F2 ```
xkill
```

---

### Post by handy on 2006-10-05
You can set **Ctrl + Alt + Del** to bring up the **System Monitor** in [Automatix]("http://www.getautomatix.com/").

---

### Post by jaboua on 2006-10-05
> **jISh said:**
> If you can't "FORCE QUIT", then try this:

Open a terminal, type in *ps -e |more* and use the enter key to scroll through the list. Find your process name, then use *killall x* where x is the name of the process you want to get rid of.

Failing that, Ctrl+Alt+Backspace will restart your X server and kill any X applications.
This will send the apps a message telling them to exit (so that they can try to exit cleanly) - if it doesn't work, try "killall -9" to kill immediately.

---

### Post by Blyzzard on 2006-10-05
You can also click on [System » Administration » System Monitor] this brings up a nice little resources graph tab and processes tab that you can use to stop.. uh processes :)

---

### Post by slibuntu on 2006-10-05
I think the moral of the story is, Ubuntu is much easier to get out of a crash than Windows!

---

### Post by JGuru on 2006-10-05
You can either Terminate the application that freezes the System, Try this
 
 $ ps -ef
 
 This will list all the processes that are running in Ubuntu Linux.
 $ sudo kill <PID>

 For eg.,
 $ sudo kill 6278

  Where PID is Process ID (a number for the application that's misbehaving).
  This will terminate that application.
 
  The Windows equivalent of 'Ctrl + Alt + Del' is 'Ctrl + Alt + Backspace'.
  This will terminate all the applications & restart the X server.

---

### Post by lmo on 2007-01-03
```
CTRL + ALT + F1
```
and then
```
CTRL + ALT + DEL
```
reboots the computer right now!

```
gnome-system-monitor
```
or menu option "System Monitor" is similar to Windows CTRL + ALT + DEL

---

### Post by Hendrixski on 2007-01-03
the command line way: type in ps to see a list of processes, then identify the one you want dead, look at it's ID number, and type kill #####

---

