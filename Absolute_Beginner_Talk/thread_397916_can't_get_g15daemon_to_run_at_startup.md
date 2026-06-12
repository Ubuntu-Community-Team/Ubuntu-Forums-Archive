---
title: "can't get g15daemon to run at startup"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by sgleo87 on 2007-03-31
I got the g15daemon running without a problem but I cannot get it to run automatically at boot. I followed the [tutorial in the ubuntu forums]("http://www.ubuntuforums.org/showthread.php?t=267118&highlight=g15daemon") and used the sudo visudo command to edit the sudoers.tmp just as described, now it looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
user ALL= NOPASSWD: /usr/sbin/g15daemon

```

Then I added g15daemon to sessions>startup programs
It didn't start at boot so I ran g15daemon without sudo in the terminal and got the following error:
```
sandra@sandra-desktop:~$ g15daemon
An Error Occurred - 1 : ( Unable to write to PID file ) received
```
The g15daemon runs fine when I use sudo so I probably did something wrong when editing the sudoers.tmp file....
What does the error message mean and how do I fix it? Help :cry:

---

### Post by sgleo87 on 2007-03-31
anybody???

---

### Post by staticfist on 2007-11-05
I'm about to try this myself and have the same concern, though I'm guessing the word "user" should be replaced with your username... I'll let you know if i figure it out. Good luck :-)

---

### Post by keyboardslave on 2007-12-23
greetings,

just replace "usr" with your username.

Kind Regards,

---

