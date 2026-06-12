---
title: "gksu to get non root privileges"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Jombo on 2007-03-19
Hi all.
I'm new to ubuntu (and to  ubuntuforums.org) but not to gnu/linux in general (I use debian).
I've a problem with gksu.
I want to launch an application (firefox) of a user (userB, not root) launched as userA.
On debian I've created an application icon and inserted the line

```
gksu -u userB /path/to/application/bin
```

where /path/to/application/bin is a directory containing the bin file to launch (with permission set correctly).
When I click that icon appear the gksu interface where I put the password of userB and I can choose also if I want to keep in memory (for the session or fore ever) the password.

When I do the same thing in ubuntu (edgy) I don't obtain the same thing.
The gksu interface appear, but is different: it ask me the password of userA and it can't let me to choose if I want save the password.
Moreover it just don't work: I've inserted userA, userB and root password and it don't work.

Here my sudoers:

User_Alias     OPERATORS = userA
Cmnd_Alias    SHUTDOWN = /sbin/shutdown, /sbin/halt,  /sbin/reboot
Defaults        !lecture,tty_tickets,!fqdn
root    ALL=(ALL) ALL
OPERATORS ALL = SHUTDOWN


How can I solve this problem?
Thanks.

---

### Post by apjone on 2007-03-19
```

gksu -u userB "/path/to/application/bin"

```

---

### Post by Jombo on 2007-03-19
no solution?

---

### Post by apjone on 2007-03-19
does that command line not work for you?

---

### Post by Jombo on 2007-03-19
> **apjone said:**
> does that command line not work for you?

Sorry, I've not menzioned it.
It doesn't work.
The problem is also for the gui, where one can choose to save password for the session.
Why there is a lack of information about gksu on ubuntu?

---

