---
title: "problem with console"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by harys on 2006-04-02
hi, i have this error message when i log in my session in gnome : 
"could not look up internet address for harys. this will prevent Gnome for operating correctly. It may be possible to corret the problem by adding harys to the file /etc/hosts".
 Then there are two options in tabs : " log in anyway" and "try again". Try again didn't respond and when i click on log in anyway tab it opened the gnome session. another problem is that almost all task in system>administration don't work like (networking which load up on the screen and disappear) and other tasks like synaptic package manager and add applications that don't even load up (no effect when i click on)
I had this message when i tried to become root in xterm with sudo su 
" sudo : unable to lookup harys via gethostbyname ( )" need a help! thanks so much. harys

---

### Post by dcstar on 2006-04-02
[QUOTE=harys]hi, i have this error message when i log in my session in gnome : 
"could not look up internet address for harys. this will prevent Gnome for operating correctly. It may be possible to corret the problem by adding harys to the file /etc/hosts".
 Then there are two options in tabs : " log in anyway" and "try again". Try again didn't respond and when i click on log in anyway tab it opened the gnome session. another problem is that almost all task in system>administration don't work like (networking which load up on the screen and disappear) and other tasks like synaptic package manager and add applications that don't even load up (no effect when i click on)
I had this message when i tried to become root in xterm with sudo su 
" sudo : unable to lookup harys via gethostbyname ( )" need a help! thanks so much. harys[/QUOTE]
You have probably mucked up your System name, do a forum search for that last error and you should find a multitude of posts on how to fix the problem.

---

### Post by taurus on 2006-04-02
Use the LiveCD to boot your machine.  Mount the partition where /etc is and edit your /etc/hosts.  Mine looks like this
```

127.0.0.1       localhost.localdomain   localhost  taurus

```

---

