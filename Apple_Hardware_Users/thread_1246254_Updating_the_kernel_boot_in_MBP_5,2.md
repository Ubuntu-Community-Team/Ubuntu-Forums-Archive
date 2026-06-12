---
title: "Updating the kernel boot in MBP 5,2"
date: 2009-08-21
forum: Apple Hardware Users
---

### Post by swarup on 2009-08-21
I installed Jaunty on my new MBP 5,2, and according to the [Wiki guide]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#MacBookPro%205,1%20&%205,2%20and%20Ubuntu%209.04%20(Jaunty%20Jackalope)") for configuring it, one has to update the kernel boot as explained [here]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Kernel%20Boot") (I've also pasted it at the bottom of this post).

My question is, according to what the instructions say there, is one supposed to *remove* the currently existing kernel configuration lines and *replace* them with what they gave, **or** should one simply add what they gave, and let the rest remain just as it was.

Specifically, the first entry below is the new one they gave on the wiki, and the second one below it (listed as a separate code box) is the old, original one in the menu.1st file. Should I delete the second one, or leave it there along side the new one?

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            ed048d83-22dc-4516-a752-d7f77239eca1
kernel          /boot/vmlinuz-2.6.28-11-generic root=LABEL=macbook-system ro quiet splash maxcpus=1
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
```

```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		db7a919d-ae1c-4a24-b732-ebff21ee2e96
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=db7a919d-ae1c-4a24-b732-ebff21ee2e96 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

I find that now, during bootup it says it is booting to uuid "db7a919d-ae1c-4a24-b732-ebff21ee2e96", which is the name of the old kernel. So I am guessing based on this, that I need to delete this lower code box from the menu.1st file, so that it will boot to the newer one above. 

For your convenience, here are the instructions from the wiki:

> Kernel Boot

The kernel provided by Ubuntu can't boot on the Macbook v5,2 out of the box. In order to boot the kernel add the option maxcpus=1 to your grub configuration (/boot/grub/menu.lst).

Add the maxcpus option to the defoptions directive:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash maxcpus=1
```

And to your existing kernel configuration lines:

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            ed048d83-22dc-4516-a752-d7f77239eca1
kernel          /boot/vmlinuz-2.6.28-11-generic root=LABEL=macbook-system ro quiet splash maxcpus=1
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
```

---

### Post by alexmurray on 2009-08-21
I would just add the maxcpus option and leave the rest as it was rather than completely replacing it all.

---

### Post by swarup on 2009-08-22
> **alexmurray said:**
> I would just add the maxcpus option and leave the rest as it was rather than completely replacing it all.

That is indeed what I did-- added the new info and kept the old info there. When booting the computer, after the grub menu screen comes, a message comes telling what kernel is booting. And it still said "db7a919d-ae1c-4a24-b732-ebff21ee2e96" i.e. the old kernel. Whereas the new kernel would say "ed048d83-22dc-4516-a752-d7f77239eca1". 

I don't know how others have done it, but it seems like if you just leave the old stuff in the menu-1st file and add the new entry alongside it, then the old kernel continues to boot up. Now, I don't know how important it is to change to the new kernel. But if there are real advantages (are there?), then I'd like to try it. How to get it done?

---

