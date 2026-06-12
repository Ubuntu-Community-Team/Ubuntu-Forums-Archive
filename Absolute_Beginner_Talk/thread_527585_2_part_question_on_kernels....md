---
title: "2 part question on kernels..."
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-16
Hi all,

I was wondering what would be the benefit of installing kernel 2.6.22 and complete or still in development? I have 2.6.20.16

and the second part:

If I install other kernels, such as the low-latency kernel, how do I tell the /boot/grub/menu.lst file which should be the default kernel?

---

### Post by lloyd_b on 2007-08-16
> **isaacj87 said:**
> Hi all,

I was wondering what would be the benefit of installing kernel 2.6.22 and complete or still in development? I have 2.6.20.16

and the second part:

If I install other kernels, such as the low-latency kernel, how do I tell the /boot/grub/menu.lst file which should be the default kernel?

1.  If you don't know why you need the new kernel, then you probably don't need it :).  The usual reason for upgrading to a newer kernel is to get support for newer devices.  There are other reasons (such as running applications that would benefit from the low-latency kernel), but those are for a very small segment of the population.

2.  In "menu.lst", look for a line like "default 0" (usually near the beginning of the file).  This is the menu entry (0 for first, 1 for second, etc) that grub will default to unless you manually tell it otherwise. 

Lloyd B.

---

### Post by isaacj87 on 2007-08-16
> **lloyd_b said:**
> 1.  If you don't know why you need the new kernel, then you probably don't need it :).  The usual reason for upgrading to a newer kernel is to get support for newer devices.  There are other reasons (such as running applications that would benefit from the low-latency kernel), but those are for a very small segment of the population.

2.  In "menu.lst", look for a line like "default 0" (usually near the beginning of the file).  This is the menu entry (0 for first, 1 for second, etc) that grub will default to unless you manually tell it otherwise. 

Lloyd B.

Thanks for the info, will Fiesty ever receive the update to 2.6.22 or are the only options we have is to either try out the gutsy tribe/wait for the release or open up the gutsy repo and get it from there?

EDIT: BTW, I found the line you were talking about (the default question), but I'm little unsure of what the "0" is referring to...How do I know the "0" is representing 2.6.20-16 and not 2.6.20-15 or the low latency kernel? I guess to clear things up...How do I know which one is which...each kernel entry doesn't have a number next to it indicating which entry it is.

---

### Post by lloyd_b on 2007-08-16
> **isaacj87 said:**
> Thanks for the info, will Fiesty ever receive the update to 2.6.22 or are the only options we have is to either try out the gutsy tribe/wait for the release or open up the gutsy repo and get it from there?

EDIT: BTW, I found the line you were talking about (the default question), but I'm little unsure of what the "0" is referring to...How do I know the "0" is representing 2.6.20-16 and not 2.6.20-15 or the low latency kernel? I guess to clear things up...How do I know which one is which...each kernel entry doesn't have a number next to it indicating which entry it is.

I believe that Ubuntu only does "bug-fix" level kernel upgrades within a release - so that in order to get the 2.6.22 kernel, you'll either need up upgrade to Gutsy, or download and build it yourself.  I'd recommend NOT doing the latter, as a change in kernel version can affect just about everything in the system (the maintainers go through a lot of effort ensuring that all the pieces of a release work properly together).

The "0" refers to the *position* of the entry in the menu.  For example, from my menu.lst (on a Edgy box):
```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot
```

"0" would mean "Ubuntu, kernel 2.6.17-11-generic" 
"1" would mean "Ubuntu, kernel 2.6.17-11-generic (recovery mode)" 
"2" would mean "Ubuntu, kernel 2.6.17-10-generic" 
"3" would mean "Ubuntu, kernel 2.6.17-10-generic (recovery mode)"

So "default 0" boots the first menu entry, whatever it may be, "default 1" would boot the second menu entry, etc.

Lloyd B.

---

### Post by isaacj87 on 2007-08-16
Thanks...that's what I thought! I didn't want to go playing around with that file seeing how it could possibly break something. Thanks for all the useful info!

---

