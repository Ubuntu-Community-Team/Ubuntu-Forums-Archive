---
title: "Error starting the GNOME Settings Daemon"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by zantzinger on 2007-03-17
Trying the Live CD of edgy on an old Dell (5000e, 700MHz, 256RAM, ATI card)
Once it opens up the Ubuntu desktop (which doesn't display properly) I get this message:


"There was an error starting the GNOME Settings Daemon.

Some things such as themes sounds or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broekn.

GNOME will still try to restart the Settings Daemon next time you log in."



Anyone know what the problem is?

---

### Post by jbayone on 2007-03-17
A few people seem to be having this problem.  Check out these threads, hopefully they'll help [http://ubuntuforums.org/showthread.php?t=351992&highlight=GNOME+Settings+Daemon]("http://ubuntuforums.org/showthread.php?t=351992&highlight=GNOME+Settings+Daemon")
[http://ubuntuforums.org/showthread.php?t=339491&highlight=GNOME+Settings+Daemon]("http://ubuntuforums.org/showthread.php?t=339491&highlight=GNOME+Settings+Daemon")

---

### Post by zantzinger on 2007-03-17
thanx. i'll try that out

---

### Post by whistlerspa on 2007-03-20
For me this was caused by an error in /etc/network/Interfaces  

I'd installed a wireless card and it had corrupted that file somehow.  I took out the card rebooted and then shutdown. Next I put the card back in and then it worked again and my login problem was history.

I also deleted references to eth0 in my file as there was no such interface  (only eth1)

---

