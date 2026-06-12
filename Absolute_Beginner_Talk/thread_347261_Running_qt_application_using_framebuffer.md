---
title: "Running qt application using framebuffer"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by !nvincible on 2007-01-27
Hi all ,

       I don't want to use Xorg so I run my qt application ,I am therefore using framebuffer directly through command mode . 
I have done this in my menu.lst

splashimage=(hd0,8)/boot/grub/splashimages/usplash-micro.xpm.gz

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda9 ro quiet splash=silent video=intelfb:ywrap vga=0x307
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

:confused: 
What is wrong ?? I have read framebuffer howto but still I am clueless .

---

