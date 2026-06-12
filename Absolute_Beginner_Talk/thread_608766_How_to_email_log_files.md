---
title: "How to email log files?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Dertiger on 2007-11-10
What is a simple way to setup an outgoing email server in order to send log files and cron output to my gmail account?  I don't want to allow incoming mail because I don't want to deal with spam.  Is there a simple and secure way to do this?

---

### Post by PointyWombat on 2007-11-11
Hi Dertiger,

Here's one way to get it working..

Install mailx:
# sudo apt-get install mailx

Then install postfix:
# sudo apt-get install postfix

Configure postfix as satellite, include your hostname, ISP SMTP server, and pretty much the defaults for the rest (other domains, no synchronous, 127,0.0.0/8, 0 limit, +, all)

To run postfix config again if needed:
# sudo dpkg-reconfigure postfix

Then test it:
echo "mail test" | mailx -s "test subject" <your email address>

If that works, great.  Now, to mail log files you can just:
cat <some logfile> | mailx -s "some log file" <your email address>

This can be setup in cron if preferred.
Hope this helps,

PointyWombat

---

### Post by Nxion on 2008-05-02
I really have no experence in messing with CRON do you know how I would set this up?

---

### Post by FastZ on 2008-05-06
Nxion: here is a good, quick run through of how to set up cron jobs.
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

