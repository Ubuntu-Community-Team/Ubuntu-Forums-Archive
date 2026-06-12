---
title: "what is su?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-06-17
when i type su in the terminal to install java it says password so i type my password and it says 

su: Authentication failure
Sorry.
  
why?

---

### Post by Dr Small on 2007-06-17
try:
```
sudo su
```

As that should work.

Dr Small

---

### Post by Cypher on 2007-06-17
"SU" is the command used to become root when you have the Root password. In Ubuntu, if you wanted to run a single command, you'd just "sudo <command>", if you wanted to become root for a length of time then you could do "sudo su".

For both of the "sudo" commands, you'd enter your password.

---

### Post by arsenic23 on 2007-06-17
You can also use su to change the owner of a terminal window.  For instance.

sister@familybox:~$ su brother
Password: ********
brother@familybox:/home/sister$

---

### Post by zakusage on 2007-06-17
You could just use "sudo -s" to have a similar result to just using "su", or just do what I do and set a password to root to ease transition from Ubuntu and Debian.

```
sudo passwd root
```

Then you can use su to your heart's desire.

---

### Post by bapoumba on 2007-06-17
Please read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo").
For a desktop user, sudo/gksudo (CLI/GUI) have been favored by ubuntu.

---

