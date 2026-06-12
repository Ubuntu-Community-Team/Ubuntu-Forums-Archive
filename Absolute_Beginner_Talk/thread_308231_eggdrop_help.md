---
title: "eggdrop help"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-11-27
hello pplz i installed eggdrop . and its working. i want to add it to status. i mean i want to start it automatically.

---

### Post by Ecthelion on 2006-11-28
Did you try adding a startup script?

Just make a script with the command to start your program and [do like they say here]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

---

### Post by pavel_kbc on 2006-11-28
not at bootup . i am talking about at login . when i login to my ubuntu login  screen  :S

---

### Post by Ecthelion on 2006-11-28
You can add the programs to start up with your session in

System > Preferences > Sessions

Then the tab for "startup programs"

Is it that you were looking for?

---

### Post by pavel_kbc on 2006-11-28
yes but want to make a scripts 


first go to the folder then run. like this
> r00t@r00t-server:~$ cd /home/r00t/Desktop/eggdrop1.6.18
r00t@r00t-server:~/Desktop/eggdrop1.6.18$ ./eggdrop -m eggdrop.conf

i cant make it work on one line

error:
> r00t@r00t-server:/$ /home/r00t/Desktop/eggdrop1.6.18/eggdrop -m eggdrop.conf
[00:21] LANG: No lang files found for section core.

Eggdrop v1.6.18 (C) 1997 Robey Pointer (C) 2006 Eggheads
[00:21] --- Loading eggdrop v1.6.18 (Wed Nov 29 2006)
[00:21] * MSG534
r00t@r00t-server:/$ 


---

