---
title: "gnome-settings-daemon xorg scrambled keyboard"
date: 2009-12-17
forum: Apple Hardware Users
---

### Post by chrisbuntu on 2009-12-17
Hi,

When I ssh into an Ubuntu computer and forward X (ssh -Y) I can type into X11 windows normally. After I start gnome-settings-daemon the keyboard starts outputting the wrong keys when I type in X11 windows.  This is even true after I've quit the remote connection.

There doesn't seem to be a key on the keyboard that produces the correct output.  I do not have a .Xmodmap file on either computer.

```
Last login: Thu Dec 17 22:15:54 on ttys000
Chris-iMac:~ chris$ ssh -Y chris-laptop.local
Warning: No xauth data; using fake authentication data for X11 forwarding.
Linux chris-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Thu Dec 17 22:15:56 2009 from ....%eth2
/usr/bin/X11/xauth:  creating new authority file /home/chris/.Xauthority
chris@chris-laptop:~$ xterm 
chris@chris-laptop:~$ # keyboard works fine 
chris@chris-laptop:~$ gnome-settings-daemon 
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "RANDR" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

** (gnome-settings-daemon:4344): WARNING **: Unable to start xrandr manager: RandR extension is not present
chris@chris-laptop:~$ xmodmap:  unable to open file '/home/chris/.Xmodmap' for reading
xmodmap:  1 error encountered, aborting.
xmodmap:  unable to open file '/home/chris/.Xmodmap' for reading
xmodmap:  1 error encountered, aborting.
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Unable to find a synaptics device.

** (gnome-settings-daemon:4344): WARNING **: Clipboard manager is already running.

chris@chris-laptop:~$ # I didn't type xmodmap above, that was a message from gnome-settings-daemon 
chris@chris-laptop:~$ xterm 
chris@chris-laptop:~$ # keyboard produces the wrong keys 
chris@chris-laptop:~$ logout
^CKilled by signal 2.
Chris-iMac:~ chris$ xterm 
Chris-iMac:~ chris$ # still weird

```

(I hid the ip address and added the comments, but otherwise everything is unchanged)

My desktop is running Mac OS 10.6.2 but I seem to remember 10.5 had this problem too.  X on my desktop is: XQuartz 2.3.4 (xorg-server 1.4.2-apple45)

You're welcome to ask me to try things out, to better suss the situation.

Thanks for your help,
Chris

---

