---
title: "Failed to load module &quot;gnomebreakpad&quot;"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by misterfixit on 2008-02-14
Surely someone knows the answer to this problem?  This just started with the last automatic upload of new and changed items.


dave@misterfixit:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [  ###        ]Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory
Connecting to daemon [   ###       ]
==========================================================[02/14/08-18:48:35]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 397 <module>
in /usr/bin/gdesklets: line 270 parse_command
in /usr/bin/gdesklets: line 174 __open_profile
in /usr/bin/gdesklets: line 155 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 295 get_daemon
[EXC]/usr/lib/gdesklets/main/client.py

[---]  290                 daemon = connection
[---]  291                 if (daemon):
[---]  292                     break
[---]  293             except socket.error:
[---]  294                 pass
[ERR]> 295             time.sleep(0.1)
[---]  296 
[---]  297         print "\r" + " " * 40 + "\r",
[---]  298 
[---]  299         if (not daemon):
[---]  300             sys.exit(_("Cannot establish connection to daemon: timeout!\n"
[---]  301                         "The log file might help you solving the problem."))


dave@misterfixit:~$

---

### Post by Gnometallix on 2008-02-17
Hi there, I am actually having a problem in which the same error comes up:

Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory

This happens when trying to do the following
sudo gedit /etc/sudoers

After I get the error, it opens the sudoers-file in read-only mode.

Hope someone can help us out?

---

### Post by Gnometallix on 2008-02-17
It might have something to do with Java.
I got the error after installing Java and the following programs using it:
-Jajuk
-Unison-gtk
-fcgui (freecrypt)

Something really annoying is that I can't use 'sudo nautilus' anymore:

```
arno@arno-laptop:~$ sudo nautilus
Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory
Initializing gnome-mount extension
arno@arno-laptop:~$
```

It doesn't ask me for a password and I don't get the rights when it opens Nautilus.

UPDATE:

```
arno@arno-laptop:~$ gksu nautilus
Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory

(nautilus:8873): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension
```

---

