---
title: "Windows access via GRUB lost"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by RobHK on 2008-01-11
My GRUB menu has been changed, though I don't know why, and Windows has disappeared from it. Ubuntu Recovery Mode and MemTest, which I had either commented out or deleted have reappeared.  It happened after an update, but this may be irrelevant.

I have SuperGrub so I can access Windows using this, but I can't get my old GRUB back.

Here is the extract from the relevant section of menu.list:

[I]title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6bfd169-0a80-47d4-920c-247bdad27c01 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6bfd169-0a80-47d4-920c-247bdad27c01 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet[/I]

What should I insert in order to have Windows included again? I have XP Home on the first partition of the first disk.

---

### Post by jken146 on 2008-01-11
This assumes Windows is installed on the first partition of your first drive (which is usually true):

After this line: ### END DEBIAN AUTOMAGIC KERNELS LIST

add these lines:

```
title Microsoft Windows XP
root (hd0,0)
makeactive
chainloader +1

```

---

### Post by RobHK on 2008-01-11
Thanks. I haven't fixed it yet but I recognize it. 

I'm curious as to what the last 2 lines mean.

---

### Post by chips24 on 2008-01-11
you can also try > bootrec /fixboot
bootrec /fixmbr using youre vista disk under command prompt, than re-install GRUB.:)

---

### Post by RobHK on 2008-01-11
Thanks. Yes, I know about fixmbr (and its terrifying warning message!). But it's not what I wanted here, as I wanted to keep the GRUB.

---

### Post by logos34 on 2008-01-11
> **RobHK said:**
> Thanks. I haven't fixed it yet but I recognize it. 

I'm curious as to what the last 2 lines mean.

In order to boot windows the partition needs to be active (or flagged 'boot' (*)-->run sudo fdisk -l).  Grub merely chainloads the NTLDR ('+1' tells it to look on the first sector of XP partition).

[http://www.gnu.org/software/grub/manual/grub.html#chainloader](http://www.gnu.org/software/grub/manual/grub.html#chainloader)
[http://www.gnu.org/software/grub/manual/grub.html#makeactive](http://www.gnu.org/software/grub/manual/grub.html#makeactive)

So you still haven't gotten XP to boot using the entry jken146 provided above?  What's fdisk show?

---

### Post by RobHK on 2008-01-11
"So you still haven't gotten XP to boot using the entry jken146 provided above?"

Yes I have, thanks. I didn't express myself clearly. I meant that I hadn't actually done it yet, but I was going to.

---

