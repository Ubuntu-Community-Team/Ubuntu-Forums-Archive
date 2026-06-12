---
title: "Help with su rights"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by KeeperMustDie on 2007-03-20
Hi, when I trying to access to su rights ant typing my password I get error: "
su: Authentication failure
Sorry."
  What am I doing wrong?

---

### Post by Bachstelze on 2007-03-20
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by KeeperMustDie on 2007-03-20
I do not understand: there is written that the password is my administrator password, my administrator password normally works on sudo commands, but it isn't working with su.

---

### Post by hyper_ch on 2007-03-20
the root user is not enabled by default on Ubuntu because you have sudo available.

---

### Post by sigge on 2007-03-20
Ubuntu does not use su, but rather do this:
```
sudo command etc
```
For instance:
```
sudo apt-get install gnome-desktop
```
The sudo program will then ask for your password. This is _your_ user-password. Ubuntu locks the root account as mentioned in the wiki linked above.

This is somewhat different from other distroes, who usually allow su, and other forms of root log-in...

Hope this helps.:)

---

### Post by mcduck on 2007-03-20
You can't use 'su', as it would ask for root password, not your own like 'sudo' does. Running 'sudo su' would work, but it's better to use 'sudo -i' instead, as that loads root's environment correctly while 'sudo su' doesn't.

---

