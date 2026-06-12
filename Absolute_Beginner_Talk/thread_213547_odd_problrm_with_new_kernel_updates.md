---
title: "odd problrm with new kernel updates?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-11
I saw that there were alot of updates today on my ubuntu box which is running the 686 kernel it updated to the latest version of the 686 kernel.No my kubuntu box is also running the 686 kernel but it wants to only update the 386 kernel updates..Anyway of fixing this so that it downloads the 686 kernel updates and smp updates

---

### Post by jonrkc on 2006-07-12
I ran into the same or very similar problem: After reading about the security-related update to the kernel, I ran dist-upgrade, but when I attempted to boot into the new kernel, I got a grub message "File missing" and discovered there is no vmlinuz-2.6.15-26-686 file in /boot, only vmlinuz-2.6.15.-26-386.  

So now, where I had been running with a 686 kernel, I'm back to a 386 one, which doesn't seem right.  

What went wrong?

---

