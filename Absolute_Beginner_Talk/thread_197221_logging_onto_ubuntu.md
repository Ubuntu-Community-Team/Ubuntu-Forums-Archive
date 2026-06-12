---
title: "logging onto ubuntu"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by stone80 on 2006-06-15
ok i've never used linux before, i finally got ubuntu installed and i rebooted and tried to logon. it said logon so i put in my user name then it asked for the password and i put it in, so now it shows my username on the command line. now how do i get to the desktop and out of this?

---

### Post by aysiu on 2006-06-15
So it's a black screen with white text? ```
stone@ubuntu:~$
``` something like that? Type these commands: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by stone80 on 2006-06-15
ok i did all that but it said aborted after sudo aptitude install ubuntu-desktop

then i put in the sudo /etc/init.d/gdm start and it said starting gnome display manager

---

### Post by aysiu on 2006-06-15
What happened after it started GDM?

---

### Post by stone80 on 2006-06-15
it said

*starting gnome display manager...                                                     [ ok ]
stone@ubuntu:~$ _

---

### Post by aysiu on 2006-06-15
After that happens, can you try pressing Control-Alt-F7?

---

### Post by stone80 on 2006-06-15
tried it, nothing happened

---

### Post by %hMa@?b&lt;C on 2006-06-15
reboot and try 
```
startx
```

---

### Post by stone80 on 2006-06-15
unable to connect to x server

no such process (errno 3): server error

it gives me an error message before the logon screen that says xserver was not installed, is that important?

---

### Post by aysiu on 2006-06-15
Hm. Can we go back to the abort error for a second?

At what point does it abort? Is it right after you type the command or after you try to answer "yes" to installing? Is there stuff that's actually going to be installed, or does it say *ubuntu-desktop* is already the newest version?

---

### Post by allix on 2006-06-15
Hmm, sounds like you installed the server version. That means you have to install a few packages manually if you want a gui. 

sudo apt-get install ubuntu-desktop
sudo apt-get install x-window-system-core

That should be all if i remember correctly. Then you just need to type "startx" and everything should boot like normal.

---

### Post by stone80 on 2006-06-15
ayisu...

i retried the commands and this time did not get an abort. it seems to have ran everything fine and after i did the > sudo /etc/init.d/gdm start
it said > *starting gnome display manager... [ok]
and under that is stone@linux:~$

so i guess its waiting for another command now?

---

### Post by aysiu on 2006-06-15
Well... it's at this point that you're supposed to either see a login screen (a graphical one) or press Control-Alt-F7 and see a graphical login screen.

---

### Post by stone80 on 2006-06-15
that sucks, i pressed alt-ctrl-f7 and it didn't do anything. 

i also tried the commands the guy above said in case i installed the server version and it said that ubuntu-desktop is already the current version. 

does it have anything to do with xserver not being installed?

---

### Post by aysiu on 2006-06-15
Theoretically, if *ubuntu-desktop* is installed, *xserver* should also be installed.

I'm not sure what's going on.

**Edit**: I did a Google search on your xserver error. Maybe [this thread](http://ubuntuforums.org/archive/index.php/t-75742.html) might help you.

---

