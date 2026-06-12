---
title: "root"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-02-21
When installing ubunutu (i've done it twice) i have been prmopted for a user name  and password whichi use to log in..bu my root (from su root) prompts me for a pasword i have never set..hence dont know...

what's up with that??

---

### Post by mcduck on 2006-02-21
By default Ubuntu has no root (or it has, but you can't log in as root). Instead, there is 'sudo' that can be used with other commands to perform tasks that need root privileges. So, to edit file as root, use 'sudo gedit file.txt', to open nautilus file manager as root run 'sudo nautilus'. To get a root shell, run 'sudo su'. Sudo uses YOUR password, not roots.

If you need a graphical way to enter your password use 'gksudo' instead of 'sudo'.

Many people like want to have 'real' root, but there is really no need for that. Sudo allows you to do everything, and you don't neven need to log out and then log in as root to perform administration tasks.

Here's some more info about Ubuntu and root/sudo: [https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29")

---

### Post by newuser111 on 2006-02-21
access to root by su is locked by default

sudo uses your user password

sudo -i or sudo -s will give you a rootshell

---

### Post by patrick295767 on 2006-02-21
If case u mess up with the root password, instead of re-installing you can have a look in the /etc/shadow:[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)

---

