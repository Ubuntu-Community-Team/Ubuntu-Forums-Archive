---
title: "Firestarter on startup, HELP!"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-03-23
hi, i am having trouble getting firestarter to start, here is my /etc/sudoers:

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

james ALL= NOPASSWD: /usr/sbin/firestarter

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

i edited this with the command sudo visudo as instructed. i added the line:

```
james ALL= NOPASSWD: /usr/sbin/firestarter
```

and added to the startup programs the line:
```
sudo /usr/sbin/firestarter --start-hidden
```

i have also tried the line:
```
sudo firestarter
```

it still doesn't work, however when i go into the terminal and type either of those startup options i type in my password and then firestarter comes up.

errrrr....

thanks,

regards
James

---

### Post by compmodder26 on 2007-03-23
This isn't really solution for your problem of getting firestarter to start automatically, but did you know that you don't need it to start automatically?  It is just a front end for the iptables firewall ubuntu uses.  So the only time you need to have firestarter open is when you want to make changes to your firewall configuration.

edit: forgot to mention that iptables DOES start automatically.

---

### Post by webjames on 2007-03-23
I know what you are saying, but i like it because it warns me when a connection gets refused. its events log, the symbol changes to a lightning bolt.

if there is no easy way i can just start it up manually each time i want it.

thanks

---

### Post by ardchoille42 on 2007-03-23
[http://ubuntuforums.org/showthread.php?t=381907](http://ubuntuforums.org/showthread.php?t=381907)

---

### Post by webjames on 2007-03-23
> **ardchoille42 said:**
> [http://ubuntuforums.org/showthread.php?t=381907](http://ubuntuforums.org/showthread.php?t=381907)

thanks, but i'm using Ubuntu -gnome. i understand that a firewall is running all the time, but i still would like to be able to have firestarter open at startup

---

### Post by tuga on 2007-03-24
This worked for me:
[http://www.ubuntuforums.org/showthread.php?t=187899](http://www.ubuntuforums.org/showthread.php?t=187899)

---

