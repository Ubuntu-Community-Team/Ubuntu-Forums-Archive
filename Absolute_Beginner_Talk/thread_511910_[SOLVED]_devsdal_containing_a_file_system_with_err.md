---
title: "[SOLVED] /dev/sdal containing a file system with errors."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-07-28
Hi I need help, I just installed vmware on my other PC using AutoMatrix and on the reboot I get ' /dev/sdal containing a file system with errors, check forced' then it says, the programe 'apt-get' is currently not installed you can install it by typing: apt-get install apt.  But when I type it I get 'command not found' what should I do? And yes I know that using AutoMatrix is not looked on favorably here but I do learn from my mistakes .

Thanks
Repent

---

### Post by rillip on 2007-07-28
Hrm, sounds like after your install fsck ran.  If seom sectors were makred as bad I guess it's conceivable that apt-get really is gone, but it seems unlikely.  Have you tried booting into recovery mode from grub?

Checking this on the net real quickly, it seems most are able to resolve this by letting fsck run, then doing a proper reboot.

For your edification, as you may not know, you can shut down from the command line in one of the following ways

```
sudo reboot
sudo shutdown -r -now
sudo init 6
```

---

### Post by Repent on 2007-07-28
Yes I have with the same results however, I really need this fixed.

---

### Post by Repent on 2007-07-28
Anyone Please.

---

### Post by rillip on 2007-07-28
Mmm, my only other idea would be to try and boot from a livecd and actually do what it recommends; using apt-get to install itself.

---

### Post by Repent on 2007-07-28
Boot from the live cd into what?

---

### Post by PriceChild on 2007-07-28
apt isn't installed because you're in a minimal shell provided for you to repair your system.... yes great error... "apt is not installed, use apt to install it"

But anyway, I suggest you type "exit" then press enter and see what happens :)

---

### Post by Repent on 2007-07-28
Thank God I fixed it it ran fsck in recovery mod but it said to do it manually, I don't know why but I just typed fsck and it ran, said it found a problem asked if I wanted to fix it I said yes and now it's fixed.  :guitar:

Thanks everyone especially PriceChild for responding to my PM.


Repent

---

### Post by Repent on 2007-07-28
OK I forgot how to mark this as resolved, any help?

---

### Post by rillip on 2007-07-29
> **Repent said:**
> OK I forgot how to mark this as resolved, any help?

Thread tools -> mark as solved from the top.

---

