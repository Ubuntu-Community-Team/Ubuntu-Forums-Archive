---
title: "So many boot"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-06-25
Can someone help me to rid myself of so many boot option when
I first start my PC.
I have so many Ubuntu ( 5 maybe ) + Windows XP :(

---

### Post by logos34 on 2007-06-25
> **burt_57 said:**
> Can someone help me to rid myself of so many boot option when
I first start my PC.
I have so many Ubuntu ( 5 maybe ) + Windows XP :(

Just comment out the old kernels with a hash '#' mark at beginning of each line:

In a terminal type:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

(this backs up the file)

gksudo gedit /boot/grub/menu.lst 

Then make it look something like this:

> #title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot

---

### Post by diskotek on 2007-06-25
or you can use synaptic to delete old kernels. searc for "linux-image" and delete the old kernels... i'm did that many times, no trouble seemed yet :D

---

### Post by logos34 on 2007-06-25
> **diskotek said:**
> or you can use synaptic to delete old kernels. searc for "linux-image" and delete the old kernels... i'm did that many times, no trouble seemed yet :D

Yes, but you never know when you might need them to boot into ubuntu.  It's not like they take up a lot of room , so I say just keep 'em but hide 'em.

---

