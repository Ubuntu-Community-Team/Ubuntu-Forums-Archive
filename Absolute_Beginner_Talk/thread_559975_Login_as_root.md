---
title: "Login as root"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by DarkChild on 2007-09-25
In installed Feisty Fawn to learn Linux, now there is 1 Problem: when i try to login as an root( on the normal Startwindow)i get the Message "You cannot login as root on this scree" whats the right Screen/option to login as root.


________________________________________________________________________________
Sorry fpor my bad English i'am from Germany and since there is no working german Forum itry to get my Help on this Forum :)

---

### Post by bobplano on 2007-09-25
that's because there is no need for a root account usually.  you can do any root things you need with sudo (more about sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo))
[to enable/do stuff with root]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_set.2Fchange.2Fenable_root_user_password")

---

### Post by HermanAB on 2007-09-25
$ sudo -i
password
#

---

### Post by Pumalite on 2007-09-25
sudo su
password

---

### Post by 3chris on 2007-10-08
I have the same problem, I know how to login in as root in the terminal, however, I need to use the GUI to perform certain tasks, how do I login in as root in the GNOME or KDE?

---

### Post by Linux_Man on 2007-10-08
Type in gksudo nautilus to have the filebrowser come up as root, that usually allows me to do what I need when I need to be root:guitar:

---

### Post by Nekiruhs on 2007-10-08
Just type ```
gksudo applicationname
``` in Gnome and ```
kdesu applicationname
``` in KDE.

---

