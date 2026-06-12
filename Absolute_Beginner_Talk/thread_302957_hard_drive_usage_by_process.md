---
title: "hard drive usage by process"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by dissdigg on 2006-11-19
I would like to know what processes are using my hard disk at any given moment.

In windows (2000/XP/etc.) by looking in Task Manager, you could select the I/O read/write columns, and see which process was accessing or writing to the hard disk in real time.  Is there something similar to this in Ubuntu?

The reason is that I'm running on on a laptop, and I'd like to keep the hard disk in standby or sleep mode, but a few minutes after I initiate a hdparm command to put it in one of these modes, it spins back up!  I'd love to know why this is happening because the system is basically idle (should be, at least).  Any other suggestions on troubleshooting this issue would be greatly appreciated!  Thanks!

---

### Post by David_T on 2006-11-19
The terminal command ``top'' will give you real-time information about your processes, similar to Task Manager.  Reading the man page should give you some information about how to interpret each of the displayed columns.  

Check out /etc/cron.daily for some scripts that may run in the background causing disk usage.

---

### Post by dissdigg on 2006-11-19
Thanks, but I think I found my problem.

Apparently there's some bug in the Ubuntu and/or laptop_mode which has been around for years:
[https://launchpad.net/distros/ubuntu/+bug/17878](https://launchpad.net/distros/ubuntu/+bug/17878)

It's too bad.  My laptop drive spins up and down a half-dozen times per minute and there's no fix.  I tried killing every process possible, but for some reason something wants to write to/acces the hard drive causing it to keep spinning back up.  I'm sure this can't be good for the hardware ](*,)

---

