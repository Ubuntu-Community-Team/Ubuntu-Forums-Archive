---
title: "Gutsy won't startup :("
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by D_D_T on 2008-02-14
I've been using Gutsy for a while now and its been working well, but after the "important security update" yesterday that required a restart, my computer won't startup.
When I turn it on, the initial Toshiba boot screen boots, and then the Grub initializes, but then it just says "Starting..." and a flat cursor ( _ ) just flashes and the hard drive does nothing. The computer still boots off a live CD, just not off the GRUB. Any suggestions as to what I can do/what may be wrong?
I don't want to do a complete reinstallation as I have important stuff on my computer and don't want to loose it.
Thanks for your help,
D_D_T

---

### Post by jan quark on 2008-02-14
try to boot into the old kernel

---

### Post by D_D_T on 2008-02-14
sorry, how do I do that?

---

### Post by jaytek13 on 2008-02-14
> **D_D_T said:**
> sorry, how do I do that?

You press escape at GRUB to load up the menu, and then you can select which kernel to boot... although this doesn't really resolve your issue.

---

### Post by njparton on 2008-02-14
Look at the options that grub presents you with.  There should also be a recovery or safe option as the 2nd entry in the grub menu?

---

### Post by jan quark on 2008-02-14
hmm

try to get into the grub menu during the booting process
press esc I think
and choose the older kernel

---

### Post by D_D_T on 2008-02-14
cool. But if I just boot from the older kernal, will this have to be done every time I boot? And will the kernal just be messed up again when I next get an update?

---

### Post by PmDematagoda on 2008-02-14
The most important thing is to establish whether you can boot Ubuntu at all.

Also, future updates should not affect an older kernel.

---

### Post by D_D_T on 2008-02-14
ok. Will try to boot now. fingers crossed!

---

### Post by D_D_T on 2008-02-14
ok, so I've booted in the recovery mode from the Grub menu as you suggested, and my computer is working again. 
Does this mean that it is happy again and that all is going to be ok, or do I need to do anything else?
Thank you for your help everyone!
D_D_T

---

### Post by PmDematagoda on 2008-02-14
Did you boot the Recovery Mode of the same kernel version that you could not boot normally?

---

### Post by D_D_T on 2008-02-14
I think so. There were three options, one was to boot off a kernel (which I guess was the standard one which failed initially), one was to boot off the same kernel but in recovery mode (which is what I chose), and the third looked like a memory check.

---

### Post by PmDematagoda on 2008-02-14
Ok, now when you reach the GRUB list again, press "E" on the normal Ubuntu entry, then change the line for root to make it "nosplash" so that it looks like this:-
```
title		Ubuntu, kernel 2.6.22-10-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=f155c3b9-00c5-4a8c-9fe3-fc71fa758e61 ro quiet [COLOR="Red"]**nosplash **[/COLOR]
initrd		/boot/initrd.img-2.6.22-10-generic
savedefault
boot
```

The above is not exactly your own entry, but the change should be at the same place.

After that change is done, boot Ubuntu by pressing "B". If that works then we can make that permanent.

---

### Post by D_D_T on 2008-02-14
cool, have done all that and it booted fine. I restarted and it booted without any problems too.

---

