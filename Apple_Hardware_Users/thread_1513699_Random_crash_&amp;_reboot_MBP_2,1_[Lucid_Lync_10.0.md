---
title: "Random crash &amp; reboot MBP 2,1 [Lucid Lync 10.04]"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by coolaj86 on 2010-06-19
Short Story:
Sometime between every few days and every few hours the system crashes.

Long Story:
I recently installed a crucial 2GB dimm. So it has a 2gb and a 1gb.
I haven't had any crashing problems while running in OS X. 
I more recently installed Linux and I've been having this crash problem very sporatically the whole time.

I've run memtest86 and it passes.
I've run memtester as non-root (as non-root it just tries to allocte memmory without actually running) and it would sometimes crash while running it for just a few seconds (while trying to unsuccessfully allocate memory).
The times that it made it to the test phase it ran until I quite it.
 
I've checked the System > Administration > Log File Viewer
    messages
    syslog
    dmesg
There don't appear to be any error messages near the time of the crash (just before the boot messages).

---

