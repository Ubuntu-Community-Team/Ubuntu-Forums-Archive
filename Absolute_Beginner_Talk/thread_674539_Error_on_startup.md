---
title: "Error on startup"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2008-01-21
Just today I booted and received this message after typing in my username and password.

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-LE5QsJDaRA: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.

Now my desktop looks a little different. There's now life preserver icon up next to the email launcher on the top bar. and my battery indicator that used to be next to the clock is missing (this is a laptop)

What did I do????

Yesterday I was adjusting "advanced desktop effects settings" I had installed Eagle CAD, and the windows in Eagle were transparent. making the contents of the windows illegible. 

Thanks,
Brian

---

### Post by A4006 on 2008-01-21
I believe a simple restart would fix this(it worked for me), if you have not discovered that already.  BTW, the life preserver is due to Ubuntu using a different icon theme when it can't load the GNOME Settings Daemon.

---

### Post by ugm6hr on 2008-01-21
This is an intermittent problem with Gnome.

This worked for me: [http://ubuntuforums.org/showthread.php?p=3776732#post3776732](http://ubuntuforums.org/showthread.php?p=3776732#post3776732)

Otherwise, you can just restart X (Ctrl-Alt-Bkspace) and hope it doesn't happen again.

---

