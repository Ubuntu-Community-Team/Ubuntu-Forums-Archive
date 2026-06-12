---
title: "XWindows Through Putty?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-05-18
Is this possible? To start XWindows through Putty on my Windows box?

---

### Post by netwerx on 2007-05-18
You mean to be able to use X?
I don't believe so.

Why don't you just setup and remote connection?

---

### Post by tageiru on 2007-05-18
It is certainly possible. You install an xserver on your windows computer and forward x, with putty, so that the programs run on the linux box but are displayed in windows.

[http://www.egr.msu.edu/decs/how-to/x11-forwarding.php](http://www.egr.msu.edu/decs/how-to/x11-forwarding.php)

VNC is probably closer to what you are looking for, though.

---

### Post by lazyart on 2007-05-18
Doing it thru putty requires some commandline skills because you can't see your desktop.

Check my sig about having a secure remote X session-- it's all detailed there.  Agreed though, that VNC is likely what you'll want to do.

---

### Post by tropicflite on 2007-05-18
This doesn't specifically answer your question, but you can always just boot up the live cd and start a regular xsession from the command line like this:

ssh -X [email]username@somecomputer.com[/email]

enter your password and you're good to go.

---

