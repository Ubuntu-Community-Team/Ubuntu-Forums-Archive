---
title: "Difference between all of the boot options?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by BavarianBuilt on 2007-10-26
Well to start I'm running a dual boot with Windows XP and Ubuntu 7.10.  I just recently upgraded to 7.10 from 7.04 last week and now I am seeing a few more operating system options when I boot my machine.  The options are as follows:

Ubuntu 7.10 Kernel 2.6.22-14-generic
Ubuntu 7.10 Kernel 2.6.22-14-recovery mode
Ubuntu 7.10 Kernel 2.6.22-16-generic
Ubuntu 7.10 Kernel 2.6.22-16-recovery mode
Ubuntu 7.10 memtest86+

I've booted into both 2.6.22-14 and 2.6.22-16 and they both seem to be identical.  What is the difference between the two?  What does memtest86+ do?  Thanks for any input guys. :smile:

Gary

---

### Post by agurk on 2007-10-26
Yeah, you likely won't notice much difference. The reason for keeping the old kernel around after a kernel update is so that you can still boot with it, should the new kernel give you any problems.
After you have checked that stuff works well with the new kernel, you can safely remove the old one using Synaptic Package Manager.

---

### Post by ItsMitsHere on 2007-10-26
> **BavarianBuilt said:**
> Well to start I'm running a dual boot with Windows XP and Ubuntu 7.10.  I just recently upgraded to 7.10 from 7.04 last week and now I am seeing a few more operating system options when I boot my machine.  The options are as follows:

Ubuntu 7.10 Kernel 2.6.22-14-generic
Ubuntu 7.10 Kernel 2.6.22-14-recovery mode
Ubuntu 7.10 Kernel 2.6.22-16-generic
Ubuntu 7.10 Kernel 2.6.22-16-recovery mode
Ubuntu 7.10 memtest86+

I've booted into both 2.6.22-14 and 2.6.22-16 and they both seem to be identical.  What is the difference between the two?  What does memtest86+ do?  Thanks for any input guys. :smile:

Gary

1. recovery mode is equivalent to safe-mode.
2. when u update a kernel, a new entry is made in the grub list of the new kernel but the older kernel entry is not deleted and you can still boot through the old kernel. you can remove the old kernel but it is safe to keep atleast one kernel that worked perfectly in case your new kernel does not workout due to some bug.
3. memtest86+ option lets you check your memory (RAM) for any faults. the reason being that sometimes comps refuse to start because there is some fault in the RAM. It comes handy when you are trying to install/upgrade and when u can not, running the memtest u can make certain that weather the problem is with your install cd or RAM. Sometimes your computer runs even with a defective ram but while performing upgrade/install of a new distro, it may fail!!!

---

### Post by maniac_X on 2007-10-26
> **BavarianBuilt said:**
>   What does memtest86+ do?

Memory test to see if you have faulty modules. [http://www.memtest.org/](http://www.memtest.org/)

---

### Post by BavarianBuilt on 2007-10-26
You guys are great, thanks for the replies.  I take it "16" is the newer kernel and "14" is the older one?  I boot into "14" each time.  Should I be using the newer "16"?

---

### Post by agurk on 2007-10-26
Yes, "16" is the latest, I'd recommend you to use it if seems to work ok. If ever in doubt about what kernel version you're currently running, type 'uname -r' (without the quotes) in a terminal.

Edit: Oops, that was probably a bit too quick an answer from me. I have two kernels in my /boot/grub/menu.lst: 2.6.22-14 and 2.6.20-16.
2.6.22-14 would of course be the latest.

---

