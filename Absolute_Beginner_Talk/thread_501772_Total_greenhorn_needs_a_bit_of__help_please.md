---
title: "Total greenhorn needs a bit of  help please"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by MYUBU704 on 2007-07-15
I get this message and don't know how to fix it.
Has anyone come across this?
I tried to run in terminal but need a bit of help with command Im ruing Ubuntu 7.04
System crashes when trying to update or remove programs.
This is my second try. I reloaded Ubuntu the first time this happened. 


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks for any help.

---

### Post by deadgobby on 2007-07-15
open up the terminal and type in 
sudo dpkg --configure -a

Gobby

---

### Post by MYUBU704 on 2007-07-15
Thanks a lot for reply
I tried that but need super user privilege?
How do I get to that point?
I have looked for the settings for that and couldnt find them.

Fetched 199B in 3s (59B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
harry@harry-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
harry@harry-desktop:~$

---

### Post by reset3x on 2007-07-15
you forgot sudo

---

### Post by deadgobby on 2007-07-15
copy and paste this in the terminal

sudo dpkg --configure -a


then enter your password. It should be the password that you logg into the splash screen.

Gobby

---

### Post by MYUBU704 on 2007-07-15
**Thanks a lot**
I got out of the mess I made.

This is a great system once you get to know a bit.
It is now my #1 boot and I'm trying to get rid of Windows all together.

---

