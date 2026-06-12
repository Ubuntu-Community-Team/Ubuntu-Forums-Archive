---
title: "blank screen unable to login"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by natewhipple on 2007-10-02
changed some settings for the login window and the next time that I turned on the computer it would just go to a black screen with a spinning cursor.

I unchecked the box, Include all users from /etc/password (not) for NIS, and then added two users to the include list.

I can login as root in recovery mode on command line and then using the startx command get ubuntu to start up but it will not allow me to to change back the settings for the login window.  I get this message


GDM( the Gnome Display Manager) is not running

You might in fact be using a differnet display manager such as KDM( KDE Display Manager) or XDM
if you still want to use this feature either start GDM yourself or ask your system administrator to start GDM

is there a way to change these settings using command line?

any help would be appreciated

---

### Post by Pumalite on 2007-10-02
At the command line:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by mysticmatrix on 2007-10-02
> **Pumalite said:**
> At the command line:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

This is not a X problem. That guy just ticked off important unix process owners and now his GDM doesn't starts.

To OP: BAsically I have no idea how to achieve that tick mark back(the one you ticked off), from a CLI. Wait till some advanced user  happens to see this tread and give appropriate commands.

---

### Post by Pumalite on 2007-10-02
Have you tried:
sudo /etc/init.d/gdm start

---

