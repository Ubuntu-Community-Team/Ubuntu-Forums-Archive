---
title: "Automactically console login"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by bb002 on 2007-03-11
Here's my problem...I've got a stand-alone box with two users, me(the admin) and the guy named "emu". The system is running Feisty Fawn as a console-only install. 

Now what I am wanting is for the first terminal (tty1) to auto login as the user "emu" while the others act as normal.

I already have dosemu starting when this user logs in followed by the dos program i want to start in dosemu....Getting the first terminal to autologin is the last part on this road.

Any help would be greatly appreciated.

---

### Post by blagger on 2007-03-21
edit the file /etc/event.d/tty1 like this:

[INDENT]# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

stop on shutdown

respawn /bin/login -f emu >/dev/tty1
[/INDENT]

---

### Post by moore.bryan on 2007-04-23
*blagger, does this method work without needing to go through the "hassle" of [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication) ?*

---

