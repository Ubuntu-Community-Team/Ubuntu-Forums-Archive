---
title: "random long startups"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-06-28
Im having this problem with my startups my computer will sometimes boot up lightning fast then other times be really slow i ckecked for virus nothing there and is anyone else having problems with firefox of it randomly crashing 

any pointers of what to start with ?

---

### Post by Seisen on 2007-06-28
It might be checking your harddrive for errors when its booting up, that would explain why it is doing it randomly.

---

### Post by seetho on 2007-06-28
Find out where it is spending so much time then you may have some clue about why it is slow.  Go to the file /boot/grub/menu.lst and look for the following section:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

```

Remove "quiet splash" from the kernel line.  You will see the boot up sequence now in text mode.

---

