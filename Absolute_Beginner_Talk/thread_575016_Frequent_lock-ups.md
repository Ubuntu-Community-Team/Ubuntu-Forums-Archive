---
title: "Frequent lock-ups"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by EAL on 2007-10-13
I've had ubuntu installed for months now and it runs great, or at least it did until the last week or so.  Now programs - simple ones like the text editor - have locked up on me, and more often, the entire operating system locks up requiring a reboot.  

I have no idea where to start with troubleshooting.  One thing I do notice when booting up is a message saying "system is not clean" but it still starts up and runs fine until it freezes, which isn't that often, but it does concern me.

Another question - how can I check the health of my hard drive?

Thanks,

E

---

### Post by jnorthr on 2007-10-13
from a terminal command line you could try
dmesg
after a boot up as it has messages from the kernel and might provide some clues we can use to locate the problem.

---

### Post by Pumalite on 2007-10-13
Post:

df -h

You can do:

fdisk /dev/hdx

---

