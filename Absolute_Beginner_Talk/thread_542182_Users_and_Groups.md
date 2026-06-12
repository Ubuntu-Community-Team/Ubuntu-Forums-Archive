---
title: "Users and Groups"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by corncob on 2007-09-03
When I try to open System>Adminstration>Users and Groups I just get an empty window.  I can move it around but can't close it.  This is the same problem NAT1V3 was having in [http://ubuntuforums.org/showthread.php?t=437617](http://ubuntuforums.org/showthread.php?t=437617) 
I tried looking for the file /etc/passwd but couldn't find it even when I unhid things.  Could this have anything to do with it?  I tried to access it in terminal:
-------------------------------------------------------------------------------------
corncob@trailer:~$ gksudo gedit /etc/passwd
(gedit:6931): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
-------------------------------------------------------------------------------------
but all that did was open that same blank window.
This started after I was playing around in Administration>Login window.  I think I put everything back the way it was though.

---

### Post by ridgeland on 2007-09-04
For User Maintenance the menu runs
gksu users-admin
Have you tried that in a terminal window?
But first does your user account have sys-admin rights?  User 1000 or root?  I keep a root account even though Ubuntu like to sudo everything.

---

### Post by corncob on 2007-09-04
Thanks, Ridgeland.  I just tried gksu users-admin and got the same thing -- a blank (white) window that I can't close.  I might reinstall Ubuntu if I can't figure this out.  It might be more far-reaching than this as I've been getting blank (but this time black) windows when I open some email until I move the window around.  Also Firefox opens into a blank (black) window when I click on a link in an email.

---

### Post by ridgeland on 2007-09-04
Uck!
I would reinstall Ubuntu.  That may be faster than debugging X.

---

