---
title: "Terminal log-in"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by noid1037 on 2005-08-17
I am trying to load a program.  I log in ok to the desktop, I start the terminal window and I type in 'su'.  Next command password... I enter the login password and it comes back something like "wrong password" .....  I thought the login password would be the same as the other passwords to run/load programs.  Is there a step that I can go and reset that password for loading programs?

Thanks
baycrestfl.com

---

### Post by aysiu on 2005-08-17
[QUOTE=noid1037]I am trying to load a program.  I log in ok to the desktop, I start the terminal window and I type in 'su'.  Next command password... I enter the login password and it comes back something like "wrong password" .....  I thought the login password would be the same as the other passwords to run/load programs.  Is there a step that I can go and reset that password for loading programs?

Thanks
baycrestfl.com[/QUOTE] Use *sudo* instead of *su*.

For example. Instead of *su* password command
do *sudo* command password.

---

### Post by h4rdc0d3 on 2005-08-17
If you want to run a session as root instead of typing 'sudo' before every command you can do one of two things:


[list=1]
[*]Open a terminal and use 'sudo -s -H' as you would formerly have used 'su'.
[*]Go to Applications > System Tools > Root Terminal.
[/list]In either case the password will be the same as your user password.

---

