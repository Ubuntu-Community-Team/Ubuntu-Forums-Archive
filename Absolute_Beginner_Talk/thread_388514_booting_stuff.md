---
title: "booting stuff"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by thomas576 on 2007-03-19
ok so i click on the kernel i want to use in grub, then it shows the boot loader text, then the screen goes into a out of scan range graphic loading screen that i can't see, then i get to xwindows login, whats the screen i can't see and how do i fix it please?

thomas

---

### Post by taurus on 2007-03-19
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```
Then reboot and see if X is running this time.

```
shutdown -r now
```

---

### Post by thomas576 on 2007-03-19
ok thats what i thought but im currently in x now and using firefox so i get to x eventually just not for login screen and whatever the boot stuff is.... please advise

---

### Post by taurus on 2007-03-19
What does the line **kernel** in /boot/grub/menu.lst look like then?

Applications -> Accessories -> Terminal
```
cat /boot/grub/menu.lst
```

---

### Post by thomas576 on 2007-03-19
[HTML]## ## End Default Options ##
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.17-11-386
root            (hd2,5)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=201eb7bc-7d69-4c03-becb-d6620d48b32f ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd2,5)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=201eb7bc-7d69-4c03-becb-d6620d48b32f ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, memtest86+
root            (hd2,5)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

[/HTML]

i can see the grub text and select a kernel im thinking its gdm or something but i can't find a place to change monitor sync rate with gdm setup only what screen i want to see, right now i have it setup for autologin so i don't have to try and type without being able to see the login screen

---

### Post by thomas576 on 2007-03-19
also what is the difference between fglrx and ati video drivers and with an x800 ati card which should i be trying to configure? thanks again

---

