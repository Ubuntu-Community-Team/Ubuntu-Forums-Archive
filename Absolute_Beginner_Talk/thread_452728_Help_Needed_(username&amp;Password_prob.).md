---
title: "Help Needed (username&amp;Password prob.)"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by gozalo on 2007-05-23
Hi,

first of all I wanna thank all those who answers my questions and helped me.

now to my problem, I downloaded ubuntu via [wubi ]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html")and installed it.. during installation it asked me to chose a username and password, I choose a username and clicked "continue" it didn't then ask me to set a password. However, after installation it asked me for username and password to log in, I typed the username and left the password... it says that the username or password is incorrect..  I can't log in what should I do?

:(

---

### Post by Sparkster185 on 2007-05-23
Can you login as root user?  If so, you can change your password with the command ```
chpasswd
```.  The command takes arguments (one line at a time) in the form of ```
username:password
``` .  You need to execute that command as root, BTW.  To terminate the input, hit CTRL+D.

---

### Post by taurus on 2007-05-23
Try booting into recovery mode and at the prompt, give that username a new password, _assuming_ the username is gozalo.

```
passwd gozalo
```
Once done, reboot and see if you can log in as gozalo with the new password.

---

### Post by bobplano on 2007-05-23
you can also log in in recovery mode which you choose from grub and that should have the same effect as logging in as root

---

### Post by gozalo on 2007-05-23
It's either I can't login as a root user, or I don't know how ....I'm confused

I hited CTRL+D but nothing happen

---

### Post by Sparkster185 on 2007-05-23
Restart the machine.  When you're given the option of which OS to boot to, select Ubunutu (recovery mode).  this will send you to the command line, logged in as root user.  From there, follow what taurus (sorry if I misspelled) said.

---

### Post by gozalo on 2007-05-23
yah I selected Ubuntu but there's no recovery mode option *I feel stupid*

---

