---
title: "Usplash, almost there..."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Vadi on 2007-09-25
I've setup a new usplash theme, but I ran into the same problem as I had with the original one.

For some reason, the loading text is still displayed, *along* with the usplash updating - so the text is scrolling up, and I can see the bar here and there update, before more text over-rides it.

How can I make it so I don't see any of the loading text, and only see the usplash?

Thanks.

---

### Post by justleen on 2007-09-25
i think it was like this : 
edit /boot/grub/menu.list, so that is says " quiet"

but im not to sure...

---

### Post by Vadi on 2007-09-25
It already is quiet thogh:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7d89739d-da99-43b8-beb4-0d1376c5b4dc ro quiet vga=773 splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7d89739d-da99-43b8-beb4-0d1376c5b4dc ro single
initrd		/boot/initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

