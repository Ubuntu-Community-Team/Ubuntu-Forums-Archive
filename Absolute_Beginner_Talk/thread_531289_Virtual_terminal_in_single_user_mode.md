---
title: "Virtual terminal in single user mode"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-08-21
Anyone know how to open a virtual terminal when you boot onto single user mode? I tried Crtl-F2 thru Ctrl-F12, but only get a blinking cursor.
If not possible, is there a way to run multiple commands in single user mode? Such as I want to run one program and run "top" to see if the job is running an how much resource it consumes. I know this could be done in run level 5 but this is a machine I dont have any password to log in. Thanks.

---

### Post by ddrichardson on 2007-08-21
There are no extra tty's in single user mode but commands can be run and released by typing ";" after them:```
sudo apt-get install pidgin; top;
```.

---

