---
title: "Grub can boot windows?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by manmohanpv on 2008-01-07
I just want to know whether Grub can boot windows from its command prompt.

I have windows xp notebook and NTFS is its file system..when i booted my system using super grub iso..it says..

unknow partion 0 type 0x08
unlnown partition 1 type 0x12

how can boot my windows XP from grub, any help?

-thanks
manmohanpv

---

### Post by phidia on 2008-01-07
you're using the grub command interface? (if you have grub installed you can edit /boot/grub/menu.lst)

the examples in grub tell you this:
> # examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

you wouldn't type in the "#" symbol and you don't need the title either.
make sure you use the proper drive notation that grub understands i.e grub starts at zero for counting. You should be able to use the rootnoverify command in place of root too. Hope that helps.

---

### Post by CheeseEatingBulldog on 2008-01-07
When setting up dual boot machines grub is the loader, so grub does load windows partitions, although I have never used grub from the command line....thought grub was loaded before a terminal is even active.

---

### Post by manmohanpv on 2008-01-07
thanks for info, learning something new..

what about windows xp? Will it able to boot windows xp if its partition is NTFS?

---

### Post by CheeseEatingBulldog on 2008-01-07
Check out these guides, but yes it can:

[http://apcmag.com/node/5162/]("http://apcmag.com/node/5162/")

---

