---
title: "Terminal resolution"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Niloc on 2006-08-20
My mate has a IBM T21 laptop he has just installed Ubuntu 5.10.
Everything seems OK except when he tries to use the command line with ctrl-alt F1..F6 he gets a black screen but the height is wrong. He enters his name but the screen is not 'long' enough to enter his password properly, it seems to think he is trying to logon as his password.....

How can we fix this?

---

### Post by moma on 2006-08-20
Just a simple idea.

1)First, I would tune the screen it self. Does the screen has any buttons to change its height, width and alignment.

2) Edit /boot/grub/menu.lst 
$ sudo gedit /boot/grub/menu.lst 

And add "vga=791" at the end of the kernel line. Here is a sample.

```
title    Ubuntu, kernel 2.6.15-26-386
root     (hd7,0)
kernel   /boot/vmlinuz-2.6.15-26-386 root=/dev/sda8 ro quiet splash [COLOR="Red"]vga=791 [/COLOR]
initrd   /boot/initrd.img-2.6.15-26-386
savedefault
boot
```

Reboot.

Table of VESA video modes:

```
          640x480    800x600    1024x768    1280x1024    1600x1200   
8 bits 	 vga=769    vga=771    vga=773     vga=775      vga=796
16 bits vga=785    vga=788    vga=791     vga=794      vga=798
32 bits vga=786    vga=789    vga=792     vga=795      vga=799
```

---

