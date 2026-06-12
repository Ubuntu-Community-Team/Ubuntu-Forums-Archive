---
title: "startup???"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-09
how do i make applications run on startup

---

### Post by rahufnagl on 2006-09-09
goto System > Preferences > Sessions
click on the Startup Programs tab

---

### Post by sigge on 2006-09-12
I do this, but still don't see the programs present that actually start when i log in.
This might be because i have copied my homedir directly  from a different system. What file is this info stored in??

:confused:

---

### Post by bulldog on 2006-09-12
Put in your session menu startup tab the program that you want to have to start up when you login.

Should work.:)

---

### Post by eisengrimm on 2006-09-20
I also did the above - and I want to start Firestarter.

I simply wrote firestarter in the list.

It starts fine! But:
A dialog says that I haven't got the privileges to run this program - Root priv. needed.

What :confused: - I only got one user which is also admin...

ideas/answers anyone?

---

### Post by Devile on 2006-09-20
i'm not quite sure, you could go ot firestarter and right click go to properties, then permissions and grant it to everybody... or you could get into the startup source somehow, and put sudo before firestarter....

---

### Post by jordanmthomas on 2006-09-20
Quick question:  why do you want to run firestarter on startup?  Do you want to configure your firewall every time you log on?  If so, you will have to deal with the password issue (unless you run as root)....which brings me to my second point.  You aren't actually the admin account on the computer, root is.  When it asks you for passwords, it is so you can run with the same priviliges as root.

Firestarter is just a GUI to configure the already built-in and running firewall.

---

### Post by eisengrimm on 2006-09-21
> **jordanmthomas said:**
> Quick question:  why do you want to run firestarter on startup?  Do you want to configure your firewall every time you log on?  If so, you will have to deal with the password issue (unless you run as root)....which brings me to my second point.  You aren't actually the admin account on the computer, root is.  When it asks you for passwords, it is so you can run with the same priviliges as root.

Firestarter is just a GUI to configure the already built-in and running firewall.

Thanks! - you just enlightened me - I didn't know that the firewall was already running! - so - I don't need to run firestarter at every startup. 

Thanks,
Eisen aka: "The beginner"

---

