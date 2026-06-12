---
title: "No more root access"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by neodarksaver on 2007-05-14
I just lost the root access. :(

I was playing with all the account settings under "administration" -->"users and groups", and my main account just lost root access. I set my ubuntu to skip the log in screen when booting, so i can't log into root during the normal booting. And worse, when i use log out or switch user, the computer screen simply displays nothing at all. I dont know what's going on, nor how to fix it. Help needed.

Thanks in advance.

---

### Post by jargoman on 2007-05-15
I'm not sure if you are saying that you lost the ability to use commands like sudo or synaptic package manager but I'll assume thats what you mean.

try this

$ su
[enter roots password]
then
$ adduser {your username} admin

that should add you back to the sudoers list

---

### Post by jargoman on 2007-05-15
also I had problems with getting a blank screen on logout

I had to use

$ sudo gedit /etc/gdm.conf-custom
then under daemon add: AlwaysResetServer=true

might work for you as well

---

