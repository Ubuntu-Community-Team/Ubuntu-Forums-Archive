---
title: "Ubuntu sometimes won't boot..."
date: 2011-01-10
forum: Apple Hardware Users
---

### Post by watgrad on 2011-01-10
Hello - sometimes my Ubuntu Maverick installation won't boot.  I wonder if there is a way to troubleshoot this issue?

I have a MacBook Pro 7.1 set up to dual boot Mac OSX and Ubuntu Maverick using rEFIt.

Sometimes during startup, ubuntu freezes after the GRUB selection screen.  After choosing ubuntu I get a flashing cursor and nothing else happens.  

Usually, restarting the computer solves the problem and the system boots normally.  However, I suspect that this problem should be resolved before it developed into a major problem?

How does one go about troubleshooting an issue like this?

Thanks for any advice...

---

### Post by taseedorf on 2011-01-10
It could be a hardware issue causing the freeze, and for some reason, it get's resolved upon boot.  I've heard that happening on Apple Computers.... what happens is on boot Ubuntu tries something, can't do it, freezes, disables whatever it going wrong... and then on REBOOT, you get into the system, and it works, is re-enabled, and then on reboot again, it won't work..etc..  

When you get into Ubuntu I'd look at the logs.  They will tell you what is going on.

/var/logs OR....Ubuntu provides gui for logs in system administration...this will let you know.  You're welcome to post what you find and we can offer a fix.

---

### Post by alexmurray on 2011-01-10
I sometimes get the same thing (probably once every 5 times I turn my MBP5,1 on) - no idea what causes it, but like you a hard poweroff and power on usually 'fixes' it.

---

### Post by watgrad on 2011-01-10
Yes - kind of unsettling - back up daily...

As a noob to ubuntu - trying to negotiate meaning from the log files is very challenging (!) - there are so many logs with so many events listed (many events aren't even dated/timestamped).  

Aside from the boot and boot.log files are there certain ones I should be looking at - at least to start troubleshooting?

---

