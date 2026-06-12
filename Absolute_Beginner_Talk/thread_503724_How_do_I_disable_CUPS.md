---
title: "How do I disable CUPS"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by veebee on 2007-07-18
My dual boot system goes great until , during boot, it tries to start CUPS...it just hangs.

Can I edit some part of the boot files to disable cups?

---

### Post by tgalati4 on 2007-07-18
Yes, you can disable it, but more importantly, what is causing it to hang?  What errors have you seen in /var/log/cups?

To stop cups:

>sudo /etc/init.d/cupsys stop

To start or restart cups:

>sudo /etc/init.d/cupsys restart

I have found cups to stall when networking is borked.  Duplicate IP address, wrong gateway, that sort of thing.  Check that your network settings are correct.

---

