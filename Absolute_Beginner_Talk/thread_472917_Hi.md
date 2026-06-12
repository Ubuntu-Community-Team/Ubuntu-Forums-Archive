---
title: "Hi"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by bbhrrr on 2007-06-13
Hello everyone

Just an introduction.
I am a mostly self taught PC/Network technician mostly using M$ environments for 10 years.

I have become slightly bored of M$ and looking for a fresh challenge so I am just finding my way around Ubuntu at the moment, I have tried some older Linux distros in the distant past, and still remember one Linux rule.
Install the **worst** operating system first - glad to see this rule still applies. :)

And here is my Question
I gather Ubuntu has some kind of boot log, can anyone here point me in the right direction, I seem to have a few boot issues I would like to post about.

Regards
BBHRRR

---

### Post by annda on 2007-06-13
there is a nice viewer utility in system>administration>system log

the one you are most interested in is probably syslog. also the command dmesg will output past kernel activities - very useful for debugging.

---

### Post by infol on 2007-06-13
First of all - Welcome   ;)

the bootlog can be found in /var/log
type ```
cat /var/log/boot
```to see the latest bootlog. 

Also, make sure bootlogging is enabled - it's not by default in ubuntu.. use your favourite editor and edit /etc/default/bootlogd and change the value of  "BOOTLOGD_ENABLE=No" from "no" to "yes"...

good luck !

---

### Post by starcraft.man on 2007-06-13
Well, since question is already answered I'll just say Hi and welcome to the forums. Oh and glad you found the better OS as you were inferring ;).

---

### Post by bbhrrr on 2007-06-14
Thanks for the help but it did not solve the problem.

I enabled logging but it did not start logging, I started with 7.04 and upgraded to 7.06 and then all this hex code appeared during the boot messages.

Sometime it's probably best to start again I wasn't happy with my partitioning anyway, I will try starting with 7.06.

Regards

---

### Post by phr0ze on 2007-06-14
There is a 7.06??? It's not on the home page. Maybe you mean you started with 6.10 and moved to 7.04? This should not cause any problems. There is generally no reason to start over. Give the forums more time to try to solve this.

BTW: The version numbers in ubuntu stand for the year and month the version was released. 7.04 was released in April, 2007, 6.10 was October, 2006.

---

### Post by bbhrrr on 2007-06-14
Sorry about that I answered that in work and did not have the full facts at hand, actually I upgraded the kernel 2.6.20-15-Generic to 2.6.20-15-Generic and now have two entries in Grub.

The Hex code is something to do with my partitioning/drives, it continues to boot but says it won't fix this.

I edited the file **/etc/default/bootlogd** as a root user:

[I]# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes[/I]

And the log viewer displays this:

Log file **/var/log/boot** (monitored)

*(Nothing has been logged yet.)*

---

