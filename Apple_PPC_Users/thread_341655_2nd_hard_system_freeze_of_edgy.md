---
title: "2nd hard system freeze of edgy"
date: 2007-01-18
forum: Apple PPC Users
---

### Post by seatea on 2007-01-18
I am running Ubuntu 6.10- the Edgy Eft  on a PM G4 1.2Ghz with 1 GB memory. I have had two system freezes (or crashes) in the last  two days. Both happened while using Firefox 2.0.0.1, but not on the same websites. Not only was Firefox frozen, but I could not access any part of Edgy. Neither  the  keyboard or mouse was responsive. I have had to hit the reset button to regain access to the system. I have all the updates installed. I have installed gnash and its plugin and would not be surprised that it would cause Firefox to crash. It is  disturbing that my whole system is brought down by one application, if indeed gnash is the problem.  My trust in a Linux system is a little shaken. Any thoughts on this occurrence

---

### Post by ssam on 2007-01-19
see if CRTL+ALT+F1, takes you to a text termial.

if it does, log in and type
```
top
```

this will show you a list of processes. if there is one at the top and its using lots of CPU then it might be the cause of the problems. if so press 'K', and type the number from the PID (process ID) column. press enter (might need to press it twice). then press 'q' to exit top, and CTRL+ALT+F7 to get back to the desktop.

if that does not work, you could try CTRL+ALT+BACKSPACE, which should kill the X server, or CRTL+ALT+DEL (or CTRL+ALT+FN+BACKSPACE on a powerbook). which should ask the machine to reboot in a gentler fashion. (there is also CTRL+APPLE+keyboard powerbutton, which will reboot a mac)

also you should file a bug at [https://bugs.launchpad.net/ubuntu/+bugs](https://bugs.launchpad.net/ubuntu/+bugs)

---

### Post by seatea on 2007-01-20
Thanks. I decided to remove gnash and its plugin and see what happens. I couldn't do the control+alternate+delete, or backspace or any other keyboard combination as the keyboard wouldn't respond. I had to use the reset button. Another thing that surprised me was that fsck did not  run on restart. I had expected it  to run after a restarting my system using the reset  button.

---

