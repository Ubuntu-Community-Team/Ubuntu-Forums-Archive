---
title: "Ubuntu 7.04  freezes at loading screen"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Monsterworm on 2007-09-28
Hi, I'm a total newbie to Ubuntu and was quite enjoying it until I started to fiddle and things went wrong lol
Yesterday I kept getting a black screen and after a search of the internet it seemed I needed to install the nVidia driver through the restricted driver manger, so I did and haven't been able to boot up since. If I boot from the hard drive  Ubuntu freezes at the loading screen, it always stops at the third square if that makes a difference. I also tried booting from the live cd but get the following error -

Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built in shell (ash)
Enter help for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

PC - Packard Bell iextreme 9608, AMD Athlon xp2000+, 256 Ram, nVidia MX400 64MB +TV out and a 40 gb hard drive.
Can anyone help me get it back working please?

---

### Post by Jimmyfj on 2007-09-28
You can try this command:

```
sudo dpkg --configure xserver-xorg
```

---

### Post by Monsterworm on 2007-09-28
Just did that and it came back with -

/bin/sh: sudo: not found
(initramfs)

Thanks

---

### Post by Monsterworm on 2007-09-28
OK if you type it in the right place then it actually does work! lol Thank you, I now have my desktop back.

---

