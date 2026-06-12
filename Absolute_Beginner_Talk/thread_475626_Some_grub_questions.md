---
title: "Some grub questions"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-16
I have ubuntu installed on my secondary hard disk, and since i have to use m$ xp as my main, because alot of the software i need to run is there, i've gone on an adventure to streamlining the grub list. I found the following:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b237c9a-3e14-4ca3-a615-4df7b9eb9e8a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b237c9a-3e14-4ca3-a615-4df7b9eb9e8a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b237c9a-3e14-4ca3-a615-4df7b9eb9e8a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b237c9a-3e14-4ca3-a615-4df7b9eb9e8a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

I realised there are 2 types of available ubuntu, which is quite weird... anyone knows what are the diffs and can i remove it?

---

### Post by hoges on 2007-06-16
These are kernel updates. You must have updated to the latest kernel, because it keeps the older version there for safety. Ubuntu does this automatically when you use the update feature.

You could probably delete them, but I'd keep them there just in case something bad happens and you need the old settings.

---

### Post by AlexenderReez on 2007-06-16
> **hoges said:**
> These are kernel updates. You must have updated to the latest kernel, because it keeps the older version there for safety. Ubuntu does this automatically when you use the update feature.

You could probably delete them, but I'd keep them there just in case something bad happens and you need the old settings.

no need...just remove them all....becuase there already backup kernel in boot.grub....which is image.bak ...by using live cd......copy that to somewhere else...then...rename it...delete '.bak' name....then paste to that folder again......simple like that....

---

### Post by maddot on 2007-06-16
thanks very much. now i have to figure out how to make it so all i need to do is press a button to load linux instead of choosing a list... heh

---

### Post by hoges on 2007-06-16
You could just set it up as the default os so it boots automatically on startup... if you don't use windows often.

---

