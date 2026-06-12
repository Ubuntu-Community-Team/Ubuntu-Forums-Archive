---
title: "GNOME Session Manager Problem"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-28
After running Evolution mail client, upon close, I get the message: Gnome Session manager (process 14087) segmentation fault. Then the system restarts. I tried using synaptic to re-install Gnome Session Manager and got this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

W: Not using locking for read only lock file /var/lib/dpkg/lock

I am asking for help with this and would ask that if you reply please keep in mind that I am a complete noob and will need specifics about scripts, etc. Thanks.

---

### Post by Regel on 2007-01-28
> run 'dpkg --configure -a' to correct the problem.

That means: ```
sudo dpkg --configure -a
```

---

### Post by paydaydaddy on 2007-01-28
It doesn't matter now. The system completely crashed and I have to do a complete re-install. I am working from the live CD now.

---

