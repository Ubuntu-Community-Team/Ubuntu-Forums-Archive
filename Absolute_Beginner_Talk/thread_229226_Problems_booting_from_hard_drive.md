---
title: "Problems booting from hard drive"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by KGH on 2006-08-04
I have XP & Mepis on sda, Ubuntu 6.0 is on hdc. When it is booting from the HD I see can't find /modules kernel 2.6.15-26-386. It loads but the mouse doesn't work & I can't access the internet.

This what I added to /boot/grub/menu.1s

title Ubuntu at hdc1 kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
boot

The grub was installed with Mepis 6.0 & I modified the Mepis boot for Ubuntu.i tried to use some of the triple boot suggestions I found here but no luck.:confused:

---

### Post by confused57 on 2006-08-04
You could try changing the root to (hd1,0), if you're booting to the sda drive 1st.

What does this show from Mepis:

```
su
fdisk -l
```
The -l is a small "L"

---

