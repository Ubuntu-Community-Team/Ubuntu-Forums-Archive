---
title: "help recompiling kernel"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-05
im tyring to apply a bluetooth patch using this guide [http://www.holtmann.org/linux/kernel/debian.html](http://www.holtmann.org/linux/kernel/debian.html)


i get this error on step 2: 
patching file arch/sparc64/kernel/ioctl32.c
Hunk #1 succeeded at 4286 with fuzz 2 (offset -39 lines).
Hunk #2 FAILED at 5024.
patch: **** Can't rename file arch/sparc64/kernel/ioctl32.c to arch/sparc64/kernel/ioctl32.c.orig : Permission denied
freeth@nephroid:/usr/src/linux-2.4.20-mh9$ sudo su
root@nephroid:/usr/src/linux-2.4.20-mh9# 
root@nephroid:/usr/src/linux-2.4.20-mh9# 
root@nephroid:/usr/src/linux-2.4.20-mh9# 
root@nephroid:/usr/src/linux-2.4.20-mh9# sudo zcat ./patch-2.4.31-mh1.gz | patch -p1
patching file arch/sparc64/kernel/ioctl32.c
Hunk #1 succeeded at 4286 with fuzz 2 (offset -39 lines).
Hunk #2 FAILED at 5024.
1 out of 2 hunks FAILED -- saving rejects to file arch/sparc64/kernel/ioctl32.c.rej
patching file CREDITS
Hunk #1 FAILED at 1356.
1 out of 1 hunk FAILED -- saving rejects to file CREDITS.rej
patching file Documentation/Configure.help
Hunk #1 FAILED at 23204.
Hunk #2 succeeded at 21320 with fuzz 2 (offset -1950 lines).
1 out of 2 hunks FAILED -- saving rejects to file Documentation/Configure.help.rej
patching file MAINTAINERS
Hunk #1 FAILED at 347.
1 out of 1 hunk FAILED -- saving rejects to file MAINTAINERS.rej
patching file Makefile
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
patching file net/bluetooth/Config.in
Hunk #1 FAILED at 14.
1 out of 1 hunk FAILED -- saving rejects to file net/bluetooth/Config.in.rej
patching file net/bluetooth/hidp/Config.in
patching file net/bluetooth/hidp/core.c
patching file net/bluetooth/hidp/hidp.h
patching file net/bluetooth/hidp/Makefile
patching file net/bluetooth/hidp/sock.c
patching file net/bluetooth/Makefile
Hunk #1 FAILED at 16.
Hunk #2 succeeded at 19 (offset -7 lines).
1 out of 2 hunks FAILED -- saving rejects to file net/bluetooth/Makefile.rej


can anyone tell me whats up?
Thanks

---

### Post by Jussi Kukkonen on 2006-09-05
You have linux source version 2.4.20 and the bluetooth patches are for version 2.4.31. Either use compatible versions or try to cope with the rejected patches manually.

---

### Post by jinxjinx on 2006-09-08
ok made it through step two here: [http://www.holtmann.org/linux/kernel/debian.html](http://www.holtmann.org/linux/kernel/debian.html)


but im stuck on step 3. where can i find a config file?
also will these instructions work for ubuntu?

Thanks.


ps is there an simpler way to apply the bluetooth patch?

---

