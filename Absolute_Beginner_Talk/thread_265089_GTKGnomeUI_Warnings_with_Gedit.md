---
title: "GTK/GnomeUI Warnings with Gedit"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by cerverx27 on 2006-09-25
This is the situation and I am new to Linux:

[B]root@mef-desktop:~# gksudo gedit /etc/fstab

(gksudo:5527): Gtk-WARNING **: cannot open display:[/B]

The above command did not load up gedit.  Then I read that it's not recommended (or you can't) load up graphical interfaces in root profile.

So I tried this:

**mef@mef-desktop:~$ gksudo gedit /etc/fstab**

[B](gedit:5533): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

This loaded up Gedit, but gave an error?  Anyone know what might be going on here?

-cerverx27

---

### Post by xmastree on 2006-09-25
Are you at at console, rather than in the graphical interface?

If so, you can't run gedit. To edit a file from there, try nano instead.

**sudo nano /etc/fstab**

---

### Post by bulldog on 2006-09-25
> **cerverx27 said:**
> This is the situation and I am new to Linux:

[B]root@mef-desktop:~# gksudo gedit /etc/fstab

(gksudo:5527): Gtk-WARNING **: cannot open display:[/B]

The above command did not load up gedit.  Then I read that it's not recommended (or you can't) load up graphical interfaces in root profile.

So I tried this:

**mef@mef-desktop:~$ gksudo gedit /etc/fstab**

[B](gedit:5533): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

This loaded up Gedit, but gave an error?  Anyone know what might be going on here?

-cerverx27

The second way is the prefered way to do it.
The warning is a little bug which is totally harmless and can be ignored.

But using gedit as root with gksudo worked flawless for me.
I tried to open fstab the same way you did as being root and no problem.

---

### Post by cerverx27 on 2006-09-25
> **xmastree said:**
> Are you at at console, rather than in the graphical interface?

If so, you can't run gedit. To edit a file from there, try nano instead.

**sudo nano /etc/fstab**


xmastree,

Gedit can be loaded from a console (terminal) window, but for me it only worked without being logged into the "root" terminal.  I am aware that nano works, but as a learning exercise I want to know why or how to get "Gedit" to work in the terminal.

---

### Post by cerverx27 on 2006-09-25
> **bulldog said:**
> The second way is the prefered way to do it.
The warning is a little bug which is totally harmless and can be ignored.

But using gedit as root with gksudo worked flawless for me.
I tried to open fstab the same way you did as being root and no problem.

Thank you for that piece of information bulldog, it helped.  Strange that I can't get it to work in root.  Any other suggestions?


and by the way...you are all very helpful.  Thank you.

-cerverx27

---

