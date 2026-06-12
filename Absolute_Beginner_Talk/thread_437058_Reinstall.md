---
title: "Reinstall"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-05-08
HI Again
As I seem to be screwed by the dbus session service I am thinking of doing a reinstall to see if it will solve the problem.

If I do a reinstall will all the system be replaced or will the problem files only be replaced ?

I have tried to repair the files with synaptic but it identifies that there are no broken files.

Thanks

---

### Post by jfinkels on 2007-05-08
> **roylond said:**
> HI Again
As I seem to be screwed by the dbus session service I am thinking of doing a reinstall to see if it will solve the problem.

If I do a reinstall will all the system be replaced or will the problem files only be replaced ?

I have tried to repair the files with synaptic but it identifies that there are no broken files.

Thanks

If you reinstall Ubuntu, you will lose all data on your current install. You'll get a fresh install.

Have you tried re-installing dbus? ```
sudo aptitude reinstall dbus
```Can you describe your problem?

---

### Post by roylond on 2007-05-09
Everything has worked ok until now. When I shudown my computer yesterday morning it was working ok. I have just tried to start again I get to the login secrren and log in ok but then get the message
" Your session only lasted less than 10 seconds. If you have not logged out yourself it could mean that there is an installation problem or you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem."

I logged in with the Gnome failsafe and everything seemed to be ok I get the desktop and all the folders etc. but then get a message "Power manager cannot start until you start the dbus session service"

I have reinstalled dbus but still get the same message when I try to login.

Read the official Ubuntu Book but cant see where to go 

R

---

### Post by jfinkels on 2007-05-09
> **roylond said:**
> Everything has worked ok until now. When I shudown my computer yesterday morning it was working ok. I have just tried to start again I get to the login secrren and log in ok but then get the message
" Your session only lasted less than 10 seconds. If you have not logged out yourself it could mean that there is an installation problem or you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem."

I logged in with the Gnome failsafe and everything seemed to be ok I get the desktop and all the folders etc. but then get a message "Power manager cannot start until you start the dbus session service"

I have reinstalled dbus but still get the same message when I try to login.

Read the official Ubuntu Book but cant see where to go 

R

What happens when you type the following in the terminal?
```

dbus-daemon

```
Is there any error message output?

---

### Post by roylond on 2007-05-09
Hi when I do that this is what I get

roy@collie:~$ dbus-daemon
No configuration file specified.
dbus-daemon [--version] [--session] [--system] [--config-file=FILE] [--print-address[=DESCRIPTOR]] [--print-pid[=DESCRIPTOR]] [--fork] [--nofork]

I dont have a clue what it means

R

---

### Post by jfinkels on 2007-05-09
> **roylond said:**
> Hi when I do that this is what I get

roy@collie:~$ dbus-daemon
No configuration file specified.
dbus-daemon [--version] [--session] [--system] [--config-file=FILE] [--print-address[=DESCRIPTOR]] [--print-pid[=DESCRIPTOR]] [--fork] [--nofork]

I dont have a clue what it means

R

Oops, my bad. Nevermind all that. I'm afraid I don't really know how to help you from here, perhaps someone else does? Sorry :(

---

