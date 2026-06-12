---
title: "Grub Loader issue- dual booting ubuntu and backtrack"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by chris1039 on 2007-06-12
Hi. I just decided to dual ubuntu and backtrack and the install for both wasn't a big deal my only problem is once i get into the boot screen and i can pick whether i want ubuntu or backtrack. I pick backtrack and it goes to:

boot 'BackTrack'

root (hd0,0)
  Filesystem type is ext2fs. patition type 0x83
boot

Error 8: Kernel must be loaded before booting

press any key to continue..._


I'm thinking i have an error with the menu.lst in the grub folder but i just spent quite a while trying any possible senario i could for the kernel and i got nothing. So if anyone could point me in the right direction that would be great. I dont mind having to do a full reinstall just incase i majorly screwed up. 

Thanks in advance

---

### Post by Bachstelze on 2007-06-12
You must add a "kernel" line which points to the actual kernel image file, for example :

```
mfb@Ana /ubuntu $ ls boot/
abi-2.6.20-15-generic         memtest86+.bin
config-2.6.20-15-generic      System.map-2.6.20-15-generic
grub                          vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic

```

My kernel image file is vmlinuz-2.6.20-15-generic and my grub gonfig file says :

```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=57107533-fb35-4298-a5f2-6ee13cc6dbf5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

---

