---
title: "still having troubles :("
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-12-08
my desktop will not start on my laptop. i cant update or reinstall anything so i am having trouble fixing the proble. a common error that i revieve is

Updating the IM modules list for GTK+-2.10.0...Bus error (core dumped)
dpkg: error processing libgtk2.0bin (--configure):
subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by houstonbofh on 2006-12-08
Boot into the memtest and check your ram.  This looks like memory crapping out to me.

---

### Post by billybag on 2006-12-08
allocated 1240465408 bytes...trying mlock...[17184033.516000] Out of memory: kill process 8892 (memtest) score 303470 amd children.
{17184033.516000] Out of memory: Killed process 8892 (memtest).
killed

...

---

### Post by wpshooter on 2006-12-08
How much memory does your machine have ?

---

### Post by billybag on 2006-12-08
i actually dont know. the laptop was recently given to my by my dad. i have only had it for like 2 or 3 months.

---

### Post by houstonbofh on 2006-12-08
> **billybag said:**
> allocated 1240465408 bytes...trying mlock...[17184033.516000] Out of memory: kill process 8892 (memtest) score 303470 amd children.
{17184033.516000] Out of memory: Killed process 8892 (memtest).
killed

...
If this was from choosing memtest from the GRUB boot menue, your ram is junk.  Try removing one or the other, but you probably need new ram.

---

