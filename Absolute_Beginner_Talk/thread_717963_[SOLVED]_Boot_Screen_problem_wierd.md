---
title: "[SOLVED] Boot Screen problem wierd"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by 1scorpio on 2008-03-07
each time i boot I have as many as 7 of the same ubuntu choices. plus the HD space on drive 2 and 3 are incorrect. the way I see it shouldnt my only boot options be--

1start ubuntu
2restore ubuntu
3safe mode
4 use other OS
I have these options in 3 or 4 sets
ithought that if i started from scratch it would solve the prob but nooooooo it just put another set on the boot choice screen

hoping for some help please

thank you in advance::(:confused::confused:

---

### Post by taurus on 2008-03-07
Can you post your /boot/grub/menu.lst and /boot?

```
ls -la /boot
sudo cat /boot/grub/menu.lst
```

---

### Post by 1scorpio on 2008-03-07
ls -la /boot
total 16620
drwxr-xr-x  3 root root    4096 2008-03-05 03:55 .
drwxr-xr-x 21 root root    4096 2008-03-05 02:40 ..
-rw-r--r--  1 root root   82712 2008-02-12 05:53 config-2.6.22-14-rt
drwxr-xr-x  2 root root    4096 2008-03-05 03:52 grub
-rw-r--r--  1 root root 7341720 2008-03-05 03:55 initrd.img-2.6.22-14-rt
-rw-r--r--  1 root root 6773282 2008-03-05 02:24 initrd.img-2.6.22-14-rt.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  841329 2008-02-12 05:53 System.map-2.6.22-14-rt
-rw-r--r--  1 root root 1806392 2008-02-12 05:53 vmlinuz-2.6.22-14-rt
scorpio@ubuntuscorpio:~$ sudo cat /boot/grub/menu.lst

sorry it took so long. life is sooooo sweet

---

