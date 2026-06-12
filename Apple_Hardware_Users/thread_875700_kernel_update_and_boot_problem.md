---
title: "kernel update and boot problem"
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by gabric098 on 2008-07-31
I've just installed Ubuntu 8.04 on my ibook G4, I did some security update using update manager. In particular after UM updated the kernel the system ask me to restart the system. I did it and, after the loading screen (the one with Ubuntu splash and the loading bar), a console appeared to me (initramfs). I suppose that there is a problem with the boot but I can't see boot logs (/var/logs dir doesn't exit).
Any suggestion to know what is happened?

Thanks,
G.

---

### Post by tiresia on 2008-07-31
Just to understand  if your problem dipends on the kernel, at the yaboot stage 2 (# boot: ) hit tab and then choose your old Kernel (it should be something like Linux-old)

---

### Post by gabric098 on 2008-07-31
Hi,
sorry but I red your message a second after rebooting the machine. Now ubuntu loads without problems but I'm not sure that kernel update is ok. At the moment my kernel version is 2.6.24-19-powerpc is this the last available (or the updated one)? I'm sorry but I don't remember which was the "old" version.

Thanks,
G.

---

### Post by tiresia on 2008-07-31
After a Kernel Upgrade Ubuntu will store your old Kernel in /boot together with the new one.
If the Upgrade didn't work as expected, you can always use the old kernel, by choosing it in yaboot.
Anyway it seems, that your problem is solved. 
Have fun! - buona fortuna :-)

---

### Post by gabric098 on 2008-07-31
> **tiresia said:**
> 
Have fun! - buona fortuna :-)
Danke! :P

---

