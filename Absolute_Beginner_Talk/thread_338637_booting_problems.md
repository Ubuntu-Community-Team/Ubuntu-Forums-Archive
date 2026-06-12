---
title: "booting problems"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-14
My Ubuntu 6.10 freezes when it hits the screen with the bar showing progresses of loading.

If I boot in recovery I can get in by typing Exit from the grub menu. That is what I did and am typing now on the computer.

I would like to know what to do to allow it to boot normally and not have to go into recovery mode to boot ubuntu.

Thanks in advance.

---

### Post by taurus on 2007-01-14
Can you edit your /boot/grub/menu.lst from recovery mode by removing the **quiet** from the kernel entry (near the end) so you would know which process causes the problem?

```
nano -w /boot/grub/menu.lst
```

---

### Post by rbhigday on 2007-01-14
> **taurus said:**
> Can you edit your /boot/grub/menu.lst from recovery mode by removing the **quiet** from the kernel entry (near the end) so you would know which process causes the problem?

```
nano -w /boot/grub/menu.lst
```

Ok, proof I am learning before I would have just typed the code and said hey it don't work. This time I put a sudo in front of it and poof it worked
Amazing doing that made it last about 1/2 inch longer on the bar, go figure

It stops at 

```
running /scripts/local-bottom
```

---

### Post by rbhigday on 2007-01-14
errr here is that line now.

```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro splash break=bottom

```

Now I am not one for coincidences that it stop on something that had bottom in and and the statement has break bottom, i don't think that is by chance. Am I right or wrong?

---

### Post by rbhigday on 2007-01-14
HEY guess what I booted,

I removed the ```
break=bottom
``` from that line and poof here i am with no recovery boot!!!!

it was not pretty the screen looked like BLEEP but I booted.

Thanks for the help, again!!!

---

### Post by rabid9797 on 2007-01-14
glad that got you through, but removing unknown elements from boot-time doesn't sound very safe, i'd keep watching this thread and try to get some advice from an expert user to find out what you removed so it doesn't come back to hit you in the face later.:???:

---

### Post by taurus on 2007-01-14
> **rbhigday said:**
> HEY guess what I booted,

I removed the ```
break=bottom
``` from that line and poof here i am with no recovery boot!!!!

it was not pretty the screen looked like BLEEP but I booted.

Thanks for the help, again!!!

I don't even have that in my kernel entry!

---

