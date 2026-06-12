---
title: "Unable to access admin functions"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by BoneyOne on 2006-08-18
Today I installed DapperDrake on both my laptop and desktop machines. After finishing both installs I accessed some of the System/Admin functions (Disks/Netork) to get everything up and running. I did this on both machines.

Now on my laptop when I attempt to open any System/Admin functions, I see it attempt to start at the bottom stating "Starting Administrative Application" but the screen doesn't fade and present me with a password box. After about 5 seconds of the busy cursor and no prompt the "Starting..." box at the bottom disappears and the machine acts like I never tried to open it.

---

### Post by muep on 2006-08-18
Try runnign this from the Terminal:

gksudo echo

Does it give any errors?

gksudo is the program that displays the password prompt. echo is there just because of the need for a command for gksudo to run.

---

### Post by BoneyOne on 2006-08-18
Yup, seems to give error...

> sudo: unable to lookup boneyone-laptop via gethostbyname()

...I have no clue what caused it to stop being able to work.

---

### Post by BoneyOne on 2006-08-18
Fixed, seems that I removed the wrong line out of /etc/hosts via the Networking application which fubared it.

Booted up into Recovery mode, then with vi added the line 127.0.0.1 localhost MACHINENAME.

Upon reboot, I had sudo back.

---

