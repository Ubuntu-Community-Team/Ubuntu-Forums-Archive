---
title: "what does this mean?"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-05
I've been trying to solve this problem for a while a can't figure it out, when I try and initialize startx I get the following server error (see below). Can anyone shed some light on this problem.

~$ sudo startx
Password:
xauth: creating new authority file /home/chris/.serverauth.9916

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again.


Please consult the The X.Org Foundation support
at [http://wiki.X.Org](http://wiki.X.Org)
for help.

---

### Post by rado_london on 2006-05-05
As far as I know this means that you already have started startx. do pkill startx and then try it again.
I am sh*t in Xorg so I would be wrong.

---

### Post by uteck on 2006-05-05
Why are you trying to run startx as root?

The error you see is because X is already running.  It may be crashed, but it is still running.
If you are in a text console, try pressing F7 to see if that will take you back to X.  

If you just want to restart the login window use;
sudo /etc/init.d/gdm restart

Or you can start up your window manager with startx, but using your ID.  IF you run it as root, then the whole session is running as root which could be very bad.

If you want to run multiple X sessions at the same time, use gdmXnest from your running session.

---

### Post by cl3ellio on 2006-05-05
That didn't work, I get the same thing, if I just try 'startx' this is the failure I get:

~$ startx
xauth:  creating new authority file /home/chris/.serverauth.8687

X: user not authorized to run the X server, aborting.

Hope this sheds a little bit more light on it.

---

### Post by WakkiTabakki on 2006-05-05
Doesn't your X start automatically? Does you box boot into a shell and nothing else?

Just wondering why you are in the need of manually starting X...

/N

---

### Post by browndog on 2006-05-05
Hey everyone do you think it would help if he tried:

> dpkg-reconfigure xserver-xorg  ?

---

### Post by WakkiTabakki on 2006-05-06
[QUOTE=browndog]Hey everyone do you think it would help if he tried:

  ?[/QUOTE]

It's a fair bet it would, yes...

Or, rather
> *sudo* dpkg-reconfigure xserver-xorg


/N

---

