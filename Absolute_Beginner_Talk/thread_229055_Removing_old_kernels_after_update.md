---
title: "Removing old kernels after update"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-08-03
In the past when updating kernels I was still left with the old kernels, including an option to boot to them from grub. The kernel update I did today did not leave the old entry in Grub but I wanted to uninstall any unused kernals so I fired up synaptic to check. I have the following kernel images listed as installed:

Linux-image-2.6.15.26-386 installed version 2.6.15.26.46  size 62.2 MB

Linux-386 installed version 2.6.15.24
size 53.2 KB.

Linux-386 installed version 2.6.15.24
size 53.2 KB. (same item listed twice )

Now my question is should the 2 files at 53.2 KB be uninstalled? They cant be whole kernels at that size so should I just leave them alone?

Thanks
Rich

---

### Post by mlind on 2006-08-03
> **Rich3077 said:**
> In the past when updating kernels I was still left with the old kernels, including an option to boot to them from grub. The kernel update I did today did not leave the old entry in Grub but I wanted to uninstall any unused kernals so I fired up synaptic to check. I have the following kernel images listed as installed:

Linux-image-2.6.15.26-386 installed version 2.6.15.26.46  size 62.2 MB

Linux-386 installed version 2.6.15.24
size 53.2 KB.

Linux-386 installed version 2.6.15.24
size 53.2 KB. (same item listed twice )

Now my question is should the 2 files at 53.2 KB be uninstalled? They cant be whole kernels at that size so should I just leave them alone?

Thanks
Rich

linux-386 is a meta package that provides you newest 386 arch kernel and newest resricted-modules package automatically. You can safely remove it if you want. If you always want newest restircted-modules package updated along with your kernel image then don't.

---

### Post by Rich3077 on 2006-08-03
Ahhh Thanks for clearing that up for me.
I am learning one step at a time.

Peace
Rich

---

