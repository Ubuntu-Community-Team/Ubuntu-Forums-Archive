---
title: "linux-686-smp kernel panic!"
date: 2006-08-03
forum: Apple PPC Users
---

### Post by jedsen on 2006-08-03
When I try to boot a linux-686-smp kernel on my macbook, I get a kernel panic that reads something like "APIC + timer does not work". Am I doomed to simply submit a report on lkml, and not have a working computer?

---

### Post by BitTorrentBuddha on 2006-08-03
You could boot from the old 386 kernal in GRUB... Or did you mean doomed to not have a computer working to it's potential? I'm sorry I don't know anymore about the error.

---

### Post by jedsen on 2006-08-03
Yes, it's a macbook, just came in the mail today.

Thanks for the tip, I'm off to try it!

---

### Post by martinbures on 2006-08-04
The kernel panic on your Macbook is normal.  This happens to mine as well from time-to-time.  It seems to know when I really need it to boot, or if I am in the middle of changing some things on it and need to reboot to make sure that they work.  With the newest kernel, the frequency of these seems to have gone down, but it might just be my imagination.

According to here:
[http://bin-false.org/?p=17](http://bin-false.org/?p=17)
It has something to do with one of the frequency settings within the kernel.  A poster says that if you re-compile the kernel and changed this setting the problem goes away.  Therefore, I would imagine that as enough people have this problem it will probably get fixed.

---

