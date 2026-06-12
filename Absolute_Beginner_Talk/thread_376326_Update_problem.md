---
title: "Update problem"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gkimberwhite on 2007-03-04
Has anyone had any problem with updating 6.10?  I installed 6.10 and when I booted it, I was told there were 138 updates for me.  When I tried to update, the program froze up after it had downloaded the files but before it was done installing them.  When I forced it to end and checked for additional updates, it told me I was up to date.  When I rebooted however, I got an error message saying that there was a "kernel panic," and it wouldn't boot.

I reinstalled 6.10 and it acted as if it wasn't writing over an existing partition.  It was like there was nothing there.

I repeated the above process to install the 138 updates and got the same situation.  I was wondering if the 138 updates (220someting MB) were too much in a single update.  Any thoughts or suggestions?

Thanks!

---

### Post by dosmode on 2007-03-04
Can't give you any ideas as to why your system would freeze up upon updating but I haven't had any problems doing 150 updates in one instance. Sorry I could not be of any more help...

---

### Post by princeallanigue on 2007-03-05
i got that problem to.
 
**error say:**

Kernel Panic -not syncing: VFS Unable to mount root fs on un known block(0,0)
--

i follow this solution writen at* [http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)*

**saying:**

To fix that, press ‘e’ to enter Edit mode at the time of booting your grub bootloader, and then press ‘e’ on the first line

(the (hd0,0) one) to edit that. Change the last 0 to a 2, so it reads: (hd0,2). Then, press ‘b’ to boot.It’s assuming that

Ubuntu is installed on the very first partition, and sets the root to that… (hd0,0) means the first partition of the first

drive, and (hd0,2) means the third partition.

**but nothing happen**

---

### Post by gkimberwhite on 2007-03-05
Interesting.  I'll mess around with that fix tonight.  Any other thoughts/suggestions out there?

---

