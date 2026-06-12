---
title: "Changing GRUB location"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2005-06-27
Hi,

I'm an absolute beginner to Linux so don't shoot me if this is an easy one. :p I installed GRUB to hd(0) (or something like that). However, I want to move it to my linux-partition. Is it possible?

---

### Post by Xian on 2005-06-27
You can certainly do this but it would appear that you currently have it installed to the MBR, and so if you move it to a Linux partition you will need to have some method available (boot disk/floppy or other bootloader) in order to access you system. 

What exactly are you attempting to accomplish?

---

### Post by aysiu on 2005-06-27
Yes, if you tell us your end-goal, we can help you accomplish it. I can't imagine why a new Linux user would not want to have Grub on the MBR.

Did you want to put Windows' boot loader back on the MBR? Because that could be trouble.

---

### Post by Nanaki on 2005-06-28
Well, currently GRUB interferes with most of my boot methods. When I hibernate with Windows XP and turn on my computer again, there's GRUB. When I boot from partition 3 (with a special keyboard key), there's GRUB again.

So I was thinking of writing GRUB to the Linux-partition, and then writing a new bootloader to the primary Windows-partition which also refers to GRUB, leaving the MBR it was before I installed Ubuntu.

Thanks for the quick replies :)

---

