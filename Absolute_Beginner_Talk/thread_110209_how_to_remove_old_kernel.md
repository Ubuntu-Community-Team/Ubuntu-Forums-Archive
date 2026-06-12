---
title: "how to remove old kernel?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by neoflight on 2005-12-30
I recently upgraded to the latest kernel 2.6.12-10-386 from 2.6.12-9-386. 
How would I remove the old one? I couldn't do it from synaptic. Thanks.
I am using Breezy 5.10.

---

### Post by bonzodog on 2005-12-30
Is there any reason you need to remove the old kernel? It will just sit there nice and quiet otherwise. I don't bother removing old kernels when ubuntu updates the kernel.

---

### Post by jsgotangco on 2005-12-30
You can do it with synaptic. Boot your machine to your new kernel (2.6.12-10-386), then open up synaptic (as sudo user). Look for linux-image-2.6.12-9-386, mark it for removal, press apply and it'll do the rest.

---

### Post by thekiller on 2005-12-30
if you just dont want to see it then simply remove [COLOR="Red"]/boot/vmlinuz-2.6.12-9-386[/COLOR] and [COLOR="Red"]/boot/initrd.img-2.6.12-9-386[/COLOR].

Then open /boot/grub/menu.lst in any editor and remove these lines :

```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

```

But I dont see any reason for removing it, as already been mentioned.

---

### Post by neoflight on 2005-12-30
Thanks folks for the quick replies. I dont have any problem keeping it there. I removed it from the menu.lst. I was just wondering if it eats up space or anything.

This is a great place to be!!!

Neo.

---

### Post by thekiller on 2005-12-30
if u want to see whats eating up your space and how much, use this command 

```

du /whatever_folder

```

---

