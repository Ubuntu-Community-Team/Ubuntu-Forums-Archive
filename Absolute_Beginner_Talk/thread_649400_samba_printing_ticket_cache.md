---
title: "samba printing ticket cache?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-12-24
I seem very close to printing to a network printer. Samba sends the job, the printer responds, acts like it going to print then suddenly...nothing.

I'm down to one error log, and funny thing is the error log finishes with "completed successfully!"

The error in /var/log/cups/error is "cannot get ticket cache for root"

Does anyone know what the problem is here, or how to fix it?

Thank you.

---

### Post by angryfirelord on 2007-12-24
It's probably something on the Windows side of things. Here's what I got searching:

[http://mandrivausers.org/index.php?showtopic=30836&st=15]("http://mandrivausers.org/index.php?showtopic=30836&st=15")

Sounds like something with the account.

---

### Post by spiderbatdad on 2007-12-24
Seems like I've been through every how-to there is on this subject. I even got the printer to feed and spit out a blank page once.

I think it has come down to a simple proprietary drivers issue as the printer is a Dell. It might be possible to add ppd data to /smb.conf but where to get the data...

---

