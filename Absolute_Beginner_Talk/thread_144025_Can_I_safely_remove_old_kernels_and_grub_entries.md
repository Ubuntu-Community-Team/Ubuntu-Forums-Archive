---
title: "Can I safely remove old kernels and grub entries?"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by isaacf on 2006-03-13
Ubuntu's autoupdate updated the kernel and didn't remove the old one. Can I get rid of the old one without breaking anything?

---

### Post by pbaehr on 2006-03-13
I always just remove the entries from grub by editing /boot/grub/menu.lst. I know that doesn't cause any problems. I've never gone so far as to track down the actual old kernel and delete it so I can't say about that. I'm happy enough just eliminating it from the menu.

---

### Post by Brunellus on 2006-03-13
if you hav eno problems with the new kernel, you can remove it in apt/synaptic with no problems.

---

### Post by engla on 2006-03-13
Normally you keep one old version around and delete the others.

On the stable releases, breezy and so it should really not be an issue, but you know it can always happen that something doesn't work with a new kernel.. so you keep one backup.

But basically, it's safe to remove older kernels with synaptic or another package tool.

[Users of the dapper alpha previews have experienced some trouble. Some removed all old kernels before trying the new one and got bitten]

---

### Post by bluevoodoo1 on 2006-03-13
You can always comment out the older kernels in your /boot/grub/menu.lst for a tidier boot menu.
I haven't removed the old kernels that have been installed by Synaptic. (unless it's one that I have compiled myself, then I'll remove it if it's not working up to par and that hasn't given me any problems).

---

### Post by Omegatron on 2007-05-12
> **pbaehr said:**
> I always just remove the entries from grub by editing /boot/grub/menu.lst. I know that doesn't cause any problems. I've never gone so far as to track down the actual old kernel and delete it so I can't say about that. I'm happy enough just eliminating it from the menu.

Uh.  Why don't you just remove the old kernels with Synaptic?

---

### Post by earobinson on 2007-05-12
Yes you can but its usualy best to keep at least one as a backup.

---

