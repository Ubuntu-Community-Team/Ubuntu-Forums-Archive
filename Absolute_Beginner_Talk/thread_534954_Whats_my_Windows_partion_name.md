---
title: "Whats my Windows partion name"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-08-25
Im trying to set up a dual boot and I have Ubuntu and Xp install and I already installed grub over the Windows mrb. But now Im trying to add XP to the grub list but Im not sure where its at. Gpartion said it was at /dev/sda2 so I put in sda2 it dident work.
So how can I figure out what the partions name is.(I have done this before with no problem.)
Please help.
Thanks

---

### Post by Duck2006 on 2007-08-25
This may help

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by logos34 on 2007-08-25
> **Duck2006 said:**
> This may help

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

That's for mounting windows in linux--the OP referred to Grub, meaning he wants to be able to boot windows.

Your windows partition is probably **sda1 (hd0,0)**

EDIT: or if it is sda2 use **(hd0,1)**

---

### Post by Duck2006 on 2007-08-25
> That's for mounting windows in linux--the OP referred to Grub, meaning he wants to be able to boot windows.

Your windows partition is probably sda1 (hd0,0)

Sorry miss read the post.

Do a

sudo fdisk -l

to see where the boot partition is.

i would try

root (hd0,1)
__________________

---

### Post by microsoft92sucks on 2007-08-25
Thanks Duck2006 alot for the quick replay.
And I feel like a noob for not trying (hda0,0) but thats what it is.

And I would Like to add Im soory Linus Torvalds for letting this OS take my PCs sweat goodness.

---

