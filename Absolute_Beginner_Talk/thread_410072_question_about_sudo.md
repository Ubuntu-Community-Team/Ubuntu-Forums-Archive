---
title: "question about sudo"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by djork on 2007-04-15
newbie here.
just wanted to know about using sudo in the command terminal.
when i use sudo commands it asks for the password on the first command
and then im guessing it lets u do the rest without typing the password.
what i wanted to know is, do i have to log off as sudo? because i've noticed
if i went back in shortly after, it let me do stuff without giving password.
am i leaving my system compromised?if so, what do i do?thanks again.
hope it all makes sense
note-same thing applies when starting admin programs
thanks again.

---

### Post by finer recliner on 2007-04-15
sudo gives your super user priveledges for about 10 or 15 minutes before you have to login again. i dont remember the exact time span. does that help you?

---

### Post by Bachstelze on 2007-04-15
*sudo* uses a "timestamp". When you successfully run a command with it, it won't ask the password again for the next 15 minutes (by default). You can reset the timestamp, forcing *sudo* to ask for the password again at the next try, with *sudo -k*.

---

### Post by wesley_of_course on 2007-04-15
Wesley here ;


      Would this help ?  [https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

---

### Post by az on 2007-04-15
> **HymnToLife said:**
> *sudo* uses a "timestamp". When you successfully run a command with it, it won't ask the password again for the next 15 minutes (by default). You can reset the timestamp, forcing *sudo* to ask for the password again at the next try, with *sudo -k*.

The timestamp only applies to that particular shell.  If you sudo in a terminal and then open another terminal a minute later, you sill still need to enter a password in the second termial, but not in the first.  The same goes for an ssh connection, or a virtual console (CTRL-ALT-F1, CTRL-ALT-F2)

Sudo does not leave your system wide open for the duration of the timestamp....

---

### Post by djork on 2007-04-16
thank you all!

---

