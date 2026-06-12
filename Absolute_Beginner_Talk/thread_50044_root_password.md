---
title: "root password"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by sweetysugar on 2005-07-18
ok,new here
what is the root password for kubuntu?
does it have anything to do with my account password or name?
please help

---

### Post by Nequeo on 2005-07-18
[QUOTE=sweetysugar]ok,new here
what is the root password for kubuntu?
does it have anything to do with my account password or name?
please help[/QUOTE]
 I haven't used Kubuntu, but I'm pretty sure they use 'sudo' the same as Ubuntu does.

If you want to execute a command with root privaleges, just prefix it with 'sudo'. E.g. 'sudo mkdir /usr/local/apps'.

When sudo asks you for a password, enter the password of the first user you created while you were installing Kubuntu.

If any graphical programs prompt you for a password, use your own. It's likely just the graphical version of 'sudo'. 

If that doesn't work - then you've encountered a nasty bug whereby your user doesn't get added properly to the sudoers file. But we'll cross that bridge if we come to it.

If you want a root shell, you can type 'sudo -s'.

If you want an actual root password so you can log in as root, type 'sudo passwd root',
enter your own password - and then set the root password.

Cheers,

---

### Post by Burgundavia on 2005-07-18
There is an excellent little article about Sudo and Root at

wiki.ubuntu.com/RootSudo

It should answer all your questions.

Corey

---

