---
title: "need help on a few things: default session boot and dpkg"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by balote on 2006-08-15
just finish installing ubuntu yesterday it was running fine

until i ran the application that downloads updates
i rebooted to get on winxp to print some stuff and i forgot that the updates download wasnt done yet

after relogging on ubuntu again nothing shows up on the screen except the brown background and the mouse pointer

when i log in on gnome safemode everything seems normal except buttons of applications that are running does not show up in the panel

and much worse, dpkg is not working for some reason

i try to rerun the update application but its asking me to run
'dpkg --configure -a'

when i type this in i get "dpkg: requested operation requires superuser privilege"

i need to get this working because apparently i need it to install graphic drivers etc, and fix the default session log-in as well

thanks in advance

---

### Post by JerMe on 2006-08-15
get to the terminal and issue these commands:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

The reason dpkg won't work is because you didn't prepend the sudo command, which will allow you to run commands as the superuser.

---

### Post by catlett on 2006-08-15
Just to clarify the point just made, enter the command with sudo
```
sudo dpkg --configure -a
```

---

