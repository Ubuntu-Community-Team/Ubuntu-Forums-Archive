---
title: "Dual Booting Ubuntu and LFS"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by DanielJackins on 2008-02-04
I have absolutely no idea how I would do this. Could anybody explain how or give me a nudge in the right direction?

Also, how much memory should I allocate to LFS? Ubuntu will remain my primary OS, I just want to fiddle around with LFS to learn new things.

Thanks

---

### Post by yaknowwat on 2008-02-05
whats LFS?

---

### Post by jw5801 on 2008-02-05
Linux from scratch.

Just follow the book and install it to a new partition. How much I'd dedicate would depend entirely on your setup. 10Gb ought to do it, you can always extend it if need be! You'll have to play it by ear as to how to set it up. Once you've got it running you may need to add an entry to /boot/grub/menu.lst but I think that's covered in the book. You probably don't want to overwrite your Ubuntu grub with a new grub, so you won't need to install or compile any of the grub related packages.

---

