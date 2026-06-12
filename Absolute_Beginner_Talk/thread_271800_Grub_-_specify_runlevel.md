---
title: "Grub - specify runlevel"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by kurtl on 2006-10-05
Hi all, I just recently got into the linux world, installed Dapper about 1 month ago. 

What i would like is being able to choose in grub what runlevel to boot with. 

i read online that this might work, however it didn't for me:
/boot/vmlinuz-2.6.15-386 root=/dev/hda2 ro single 3 <--3 being the runlevel

if anyone could help me out or point me in the right direction i would really appreciate it!

---

### Post by bodhi.zazen on 2006-10-05
Just add the run-level number at the end of the kernel line:

Change > /boot/vmlinuz-2.6.15-8-386 root=/dev/hda34 ro quiet splash

to 

```
/boot/vmlinuz-2.6.15-8-386 root=/dev/hda34 ro quiet splash **3**
```

---

### Post by kurtl on 2006-10-05
Thanks for the quick reply, i appreciate it - i thought i tried this last night, but i will try it again and veryify the runlevel after bootup when i get home, stuck at work :(

---

### Post by bodhi.zazen on 2006-10-05
FYI: I have seen Ubuntu mis-identify runlevel 3 as 2 when you run the "runlevel" command. This has occurred when there are no differences between 2 and 3.

I tested runlevels in this situation by changing from 2 to 1 and then 3.

runlevel still returned a "2".

You may need to confirm your run level by checking what is or is not running at 3 vs. 2.

---

### Post by kurtl on 2006-10-05
awesome info, thanks again

---

