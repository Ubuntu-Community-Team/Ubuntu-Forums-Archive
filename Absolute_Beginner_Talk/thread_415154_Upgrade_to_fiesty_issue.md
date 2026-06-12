---
title: "Upgrade to fiesty issue"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by gamegenieny on 2007-04-20
I upgraded yesterday and now I can't log into my profile. Its only one particular profile (my original one) and when I log onto it it gives me a text saying that Its logging out in under 10 seconds and theres this log

etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "arch"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/arch-desktop:/tmp/.ICE-unix/7106
Initializing gnome-mount extension

** (nautilus:7173): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:7173): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:7173): WARNING **: Can not get _NET_WORKAREA

** (nautilus:7173): WARNING **: Can not determine workarea, guessing at layout

(update-notifier:7209): GnomeUI-WARNING **: While connecting to session manager:
IO error occured doing Protocol Setup on connection.

I tried to go on the profile under gnomefailsafe and all it does is log me right out. the terminal failsafe seems to work but I have no idea what to do now. Can anyone help ?

---

### Post by weijie90 on 2007-04-20
try adding a new user via the command line and logging in via that user.

---

### Post by gamegenieny on 2007-04-20
I have a few users on it, thats how I'm able to get here. I can log on to the other users with no problem, but the main user is where this problem is happening. Would it be possible to delete that user, and the problem with it ? That was the default user so what would I do as far as far as the passwords with regards to it being the root/sudo password ? If I am describing this wrong forgive my noobness. 

That user was the first one created on the system, and I believe that means it has admin privileges or whatever its called. Thats the point I'm trying to get across.

---

### Post by gamegenieny on 2007-04-20
Does anyone have an idea of what I can do to fix this ?

---

### Post by redbluemangle on 2007-04-21
Get into your tty terminals and install kde, xfce of fluxbox from the CLI until this can be resolved.

ctrl alt F2 i believe. not sure if it's a straight up "apt-get install GUI" or amybe its more. Look it up.

---

### Post by gasti on 2007-04-26
I have a quite similar problem:
```

Initializing gnome-mount extension
Initializing nautilus-open-terminal extension

** (nautilus:6530): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6530): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6530): WARNING **: Can not get _NET_WORKAREA

** (nautilus:6530): WARNING **: Can not determine workarea, guessing at layout


```

I can login but my windows are all top left of the screen without the tob bar of windows with the [X] button to close. I cannot go from a window to another: I have to close the upper one. And (what a surprise) the button to switch from aDesktop to another is reduced to vertical line.

When I connect with another user, everything is ok !?!

---

### Post by macabro22 on 2007-04-27
me too!
here's my .xsession-erros:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "macabro22"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/HAL:/tmp/.ICE-unix/8182
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Initializing gnome-mount extension

** (gnome-session:8182): WARNING **: Host name lookup failure on localhost.
** Message: failed to load session from /home/macabro22/.nautilus/saved-session-DR4TQT
Unable to open desktop file file:///usr/share/applications/evolution-mail.desktop for panel launcher: No such file or directory

** (nautilus:8255): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:8255): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:8255): WARNING **: Can not get _NET_WORKAREA

** (nautilus:8255): WARNING **: Can not determine workarea, guessing at layout
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)


** (nautilus:8255): WARNING **: Can not get _NET_WORKAREA

** (nautilus:8255): WARNING **: Can not determine workarea, guessing at layout
Reloading options
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading optiX connection to :0.0 broken (explicit kill or server shutdown).

on
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
Reloading option
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048

---

