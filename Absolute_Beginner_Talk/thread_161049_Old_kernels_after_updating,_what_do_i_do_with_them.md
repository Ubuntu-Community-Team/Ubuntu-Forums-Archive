---
title: "Old kernels after updating, what do i do with them?"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by meistwer on 2006-04-16
Hi guys,

I've updated my kernel twice since Im using Ubuntu. The question is that I still see them in GRUB when booting up, what do i do? Do i have to delete them or just leave them like that?:confused: 

Rob

'Nobody Escapes The Algebra Of The Infinite Justice'

---

### Post by htinn on 2006-04-16
You can just remove them with Synaptic or apt-get remove, etc. if you feel comfortable with the kernel you're using.

---

### Post by meistwer on 2006-04-16
Ive just check with Synaptic and it shows that the kernel aren't installed, i can only mark them for installation.... do i havre to look in 'Linux kernel image for version 2.6.x.x...' or 'Linux kernel source for version 2.6.x....'

---

### Post by htinn on 2006-04-16
I think you're looking for "linux-image-something..."

---

### Post by Mustard on 2006-04-16
Personally I would keep at least one other kernel.  Sometimes you can have an issue with booting up with your latest kernel, and having a second one in your grub menu to boot up to can be very handy at those times.  I guess it depends on whether you are short of space in your root partition.

---

