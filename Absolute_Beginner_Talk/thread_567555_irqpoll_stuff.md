---
title: "irqpoll stuff"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by brander on 2007-10-04
My Ubuntu will not boot normally from the SATA HD without the addition of irqpoll after ro quiet splash in menu.lst. Without it, it stops immediately the first orange bar appears on the progress bar.

With it, everything works fine and it boots quickly.

But every time there is a kernel update, it removes this setting and I have the problem of getting back in to edit menu.lst again. 

My hardware is common, Intel 945 chipset with Hitachi hard drive and as a lot of people seem to have this problem I don`t know why it isn`t fixed. But meanwhile, is there anything I can do to menu.lst to keep the irqpoll setting when the kernel is updated?

---

### Post by ofb on 2007-10-06
> **brander said:**
>  But meanwhile, is there anything I can do to menu.lst to keep the irqpoll setting when the kernel is updated?

From over here
[http://ubuntuforums.org/archive/index.php/t-81153.html](http://ubuntuforums.org/archive/index.php/t-81153.html)

"
If/when you find something that works, edit /boot/grub/menu.list and make the changes there. In menu.list, don't edit the kernels directly. If you do, you'll lose your changes the next time you update the kernel. Instead, edit the commented lines between ### BEGIN AUTOMAGIC KERNELS LISTand## ## End Default Options ## When you're finished, run sudo update-grub
"

However, if you do that then you won't know when your problem is fixed by a new kernel. And I suppose you could have a conflict with changes too.

---

