---
title: "[SOLVED] no password for sudo command"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by StephUb on 2007-12-06
Hi all,

I was trying to tweak xorg,conf to get my touchpad working was used to have to enter my password when sudo gedit
And at one point it stopped asking me the password and let edit xorg.conf only with sudo without password.
I tried to find info on this forum but so far just to look at my sudo visudo...
Is there something wrong?

the only line non uncommented is Defaults !lecture,tty_tickets,!fqdn

I looked into the users privileges and i am able to administer the system?

How can i put back the system to ask me the password each time i enter the sudo command ?

thank you

---

### Post by daimaru on 2007-12-06
if your in terminal and use sudo it remember it for about 10 or 5 minutes not sure. so if you use the same terminal to edit another file that needs sudo access it wont ask for the password. same thing happens with synaptic gui. if you just used it and close it down and then use it again it will not require password. not to worry its just a time thing so you don't get bothered to always input your password.
EDIT: so if you open another terminal and try to execute a sudo command you will be asked for password. only the terminal your originally entered your password in will  remember it.
its the same as this forum if you dont do anything for some time on this forum while logged in and you come back and hit refresh you'll be logged out, because your session expired.

---

### Post by akiratheoni on 2007-12-06
Good, someone worried about their security :) Most people ask how to get rid of the password, so it's good that you actually want it. But don't worry; if you use sudo, you don't need to type in your password for another about 15 minutes or so... it's there for convienence. If you're uptight about security, though, there are ways to make that length shorter, but I don't know where.

---

### Post by StephUb on 2007-12-06
Ok i checked with a new terminal and indeed, it's asking the password..

is there a way to remove that ?
I mean removing the fact that the terminal is storing the password somewhere ??

EDIT
Find "Defaults !lecture,tty_tickets,!fqdn" and replace by "Defaults timestamp_timeout=1"

Is that in minutes?

Is there a way to disable the timestamp?

---

### Post by PeterJS on 2007-12-06
It's not actually storing the password, it's storing the fact that you have entered the correct password within the time allowed. It to disable caching, add:
```

timestamp_timeout 0

```to your sudoers file.

---

### Post by FuturePilot on 2007-12-06
Both sudo and gksudo remember the password for 15 minutes so you don't have to keep retyping it.

---

### Post by StephUb on 2007-12-06
thank you i will try to mark the thread solved if i can find how to do it...

---

### Post by StephUb on 2007-12-06
and i found it pretty easily

thank you again for the help

---

