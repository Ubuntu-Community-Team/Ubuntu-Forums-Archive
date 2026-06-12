---
title: "KDE Control Center problems"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by jhamer9 on 2005-11-16
Hello Forum!  This is my first post here at ubuntu forums.

I am fairly new to Linux, but know where some config files live and a few basic commands.

I've recently installed Kubuntu Hoary Hedgehog 5.04 on a Compaq Armada M700 laptop.

I'm trying to get into administrator mode in the control center on a few moduels, the network settings module and the wireless network module don't seem to be accessible.  They open, but after clicking on the administrator mode button and typing in the sudo password, it just takes me back to the previous menu selection and the controls are greyed out.

At first I thought the obvious, the sudo password I'm typing isn't correct, but that same password works when I'm using the command line utilities.

I then tried to launch " sudo kcmshell kcm_knetworkconfmodule" from a konsole typed in my password and saw the following:
"sudo kcmshell kcm_knetworkconfmodule
Password:
Error: "/var/tmp/kdecache-*username*" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"

Does the admin gui utilites use a different username and password than the orginal account created during install?  Any help would be appreciated.  Thanks.

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=jhamer9]Hello Forum!  This is my first post here at ubuntu forums.

I am fairly new to Linux, but know where some config files live and a few basic commands.

I've recently installed Kubuntu Hoary Hedgehog 5.04 on a Compaq Armada M700 laptop.

I'm trying to get into administrator mode in the control center on a few moduels, the network settings module and the wireless network module don't seem to be accessible.  They open, but after clicking on the administrator mode button and typing in the sudo password, it just takes me back to the previous menu selection and the controls are greyed out.

At first I thought the obvious, the sudo password I'm typing isn't correct, but that same password works when I'm using the command line utilities.

I then tried to launch " sudo kcmshell kcm_knetworkconfmodule" from a konsole typed in my password and saw the following:
"sudo kcmshell kcm_knetworkconfmodule
Password:
Error: "/var/tmp/kdecache-*username*" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"

Does the admin gui utilites use a different username and password than the orginal account created during install?  Any help would be appreciated.  Thanks.[/QUOTE]


use 

```
gksudo
```

instead of 

```
sudo 
```

and see if it works.

---

### Post by jhamer9 on 2005-11-16
thanks for the reply.

gksudo returned a bash error: command not found

i then ran kdesu and received the following error, which I remember seeing after a reboot.

```
 DCOP Communications Error (KDE Control Module)

Authentication Rejected, reason: None of the authentication
protocols specified are supported and host-based authentication failed 

please check that the "dcopserver" program is running!
```

That can't be good...

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=jhamer9]thanks for the reply.

gksudo returned a bash error: command not found

i then ran kdesu and received the following error, which I remember seeing after a reboot.

```
 DCOP Communications Error (KDE Control Module)

Authentication Rejected, reason: None of the authentication
protocols specified are supported and host-based authentication failed 

please check that the "dcopserver" program is running!
```

That can't be good...[/QUOTE]

Cool. I have an idea. Lets make a root user for you:

[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

See if that fixes it.

---

### Post by jhamer9 on 2005-11-16
Thanks!  That seemed to fix the problem.  quick question, should i now disable the root password using

```
sudo passwd -l root 
``` 

or just let it be?

---

