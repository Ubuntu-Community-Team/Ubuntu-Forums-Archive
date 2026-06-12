---
title: "where r all the programs?"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by cool disel on 2005-08-12
hi yall,  how'r u all doin'?  i know that what about to ask is kinda of dull.. but in my defence i still new in using ubuntu.. 


my question is Where r all the program files?" like in Windows they have program files folder.. but in ubuntu i kept looking for it but i couldn't fund it:(

---

### Post by Ampersand on 2005-08-12
the programs in linux are spread throughout the /usr folder. Most of the executables are in /usr/sbin , and the configuration files are in /etc. However, just about anything you install using Synaptic or apt-get will appear in the menu.
Richard

---

### Post by cool disel on 2005-08-12
thanx alot mate....  the reason i'm looking for the executables because i want to add some programs to the startup programs' list :)

---

### Post by wmcbrine on 2005-08-13
Most are in /usr/bin. /usr/sbin is for system administration-related stuff. Some others are in /bin, /usr/X11R6/bin, and various other places. Type "echo $PATH" on the command line to get a list of executable directories checked by the shell.

---

### Post by gb25 on 2005-08-13
If you are looking for the location of a particular program and know the executable name, then you can use whereis and it'll tell you where it's at.  For example:

```
gary@400sc:~$ whereis firefox
firefox: /usr/bin/firefox /usr/share/man/man1/firefox.1.gz
```

---

