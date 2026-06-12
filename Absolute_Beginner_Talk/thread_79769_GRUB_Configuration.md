---
title: "GRUB Configuration"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2005-10-20
To start off with, I wanted to try out other flavours of Linux other that Ubuntu (heresy, I know... ), so i went and installed Mepis after hearing good things about it. 
After installation, GRUB no longer gave me the choice of booting Ubuntu anymore. 

I think I have to edit some grub configuration file, to be given the choice or booting Ubuntu again, but i dont know which one it is nor what to change so I though id come here for help, as the Ubuntu community has never been less than amazingly friendly.

---

### Post by xristos on 2005-10-20
Edit your /boot/grub/menu.lst file and add the following assuming ubuntu is on the first partition on your first hard drive and we have the same kernel image name .

```
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
```

---

