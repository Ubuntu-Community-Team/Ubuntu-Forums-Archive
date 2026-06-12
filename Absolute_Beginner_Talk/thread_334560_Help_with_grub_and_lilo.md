---
title: "Help with grub and lilo"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-09
Hi, i am currently running grub but wish to switch to lilo. I have grub installed to my linux (active) partition. I installed lilo to the same partition but grub still runs instead of lilo. How do i disable grub and enable lilo?

---

### Post by sardion on 2007-01-09
I think you just need to do 

sudo lilo -v

assuming you have lilo installed and its config files set up etc.

---

### Post by ajmorris on 2007-01-09
thanks for the reply but i just installed a boot manager and now i can boot into either.

Except now lilo won't boot and it says it can't mount root filesystems. and there was an error with /sbin/init?

---

