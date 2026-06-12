---
title: "How to find my root password?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by neo-monarchist2 on 2007-01-22
I am trying to do a process that requires the use of the root account, but I do not know my root password. I tried entering the password for my main account that I installed Ubuntu with, but this did not work. If I recall correctly, I was never asked to create a password other than the main account that I am using. How should I go about finding my root password out?

---

### Post by wildkarde on 2007-01-22
There is no root password.  Anything that you need to do using a root account can be done by  running the command sudo.

example: lets say you need to run apt-get update as root.  You would do this:
```
sudo apt-get update
```

It will ask you for a password.  It's asking at this point for your login password.

Hope this helps.

---

### Post by Shatrat on 2007-01-22
There is no root account in ubuntu.
Here is some reading that might clear it up.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What are you trying to do?  Maybe we can help translate the intructions into ubuntu appropriate commands

---

### Post by bodhi.zazen on 2007-01-22
For graphical programs 

Gnome : gksudo

KDE : kdesu

Termainal : sudo

Change to root (in a terminal) : sudo -i

Set Root PW : sudo passwd

---

