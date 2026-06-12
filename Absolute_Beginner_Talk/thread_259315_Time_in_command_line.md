---
title: "Time in command line"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Klemik on 2006-09-17
Is there any way to place time into command line ?
Eg. 13:45:43 Username@ComputerName:~$

---

### Post by gborzi on 2006-09-17
Yes, by modifying the PS1 shell variable, that is defined in ~/.bashrc . To have the time as in your example add a \t (24h format) before the \u in PS1. E.g. currently in .bashrc you have
> PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
change this to 
> PS1='${debian_chroot:+($debian_chroot)}\t \u@\h:\w\$ '
Alternatives to \t are:> \t     the current time in 24-hour HH:MM:SS format
              \T     the current time in 12-hour HH:MM:SS format
              \@     the current time in 12-hour am/pm format
              \A     the current time in 24-hour HH:MM format
from bash manpage.

---

