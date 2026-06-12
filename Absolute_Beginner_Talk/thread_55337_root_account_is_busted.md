---
title: "root account is busted"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by z3r0-c0d3r on 2005-08-08
I changed the themes and installed KDE and after switching it on today when I log into root the two bars on top and bottom just blink and nothing happens??
but all other accounts work!
and everything loads twice on the splash screen including nautilius and gaim and rthymbox and stuff

---

### Post by eivind on 2005-08-08
I could be wrong, but to my knowledge, this is a feature and not a flaw. You shouldn't be able to log in as root on a default Ubuntu or Kubuntu installation, we use "sudo" instead whenever we need to run commands as root. That's probably why you're experiencing problems.

Cheers,

Eivind

---

### Post by poofyhairguy on 2005-08-08
Its not busted, Ubuntu lacks one by default (like OSX)

[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

---

### Post by z3r0-c0d3r on 2005-08-09
i already added a root account so i can install easily without typing my password over and over again, it worked fine but now it doesn't!

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=z3r0-c0d3r]i already added a root account so i can install easily without typing my password over and over again, it worked fine but now it doesn't![/QUOTE]

you can do this command:

sudo -s

---

### Post by mohsin on 2005-08-09
how to login to root acount .. .. 

 i have account name ubuntu pwd 123 

 but i want to use root how could i

---

### Post by Tom Fury on 2005-08-09
Take a look at this thread.

[http://www.ubuntuforums.org/showthread.php?t=31053&highlight=enable+root+account](http://www.ubuntuforums.org/showthread.php?t=31053&highlight=enable+root+account)

---

### Post by z3r0-c0d3r on 2005-08-10
I think i figured out the problem but i need to know if there is a way to alter the root accounts startup programs without logging on because when i logon with kde into root it works perfectly.
does any one know how to do this??

---

