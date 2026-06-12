---
title: "[SOLVED] GRUB Overwritten"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Xavieran on 2008-01-11
I installed Arch Linux on a separate partition to Ubuntu and now I can't access my Ubuntu partition...I get a GRUB error 13 Invalid or Unsupported file format...

The settings for Ubuntu in GRUB are:

rootnoverify (hd0,0)
makeactive
chainloader +1

What should I change?
Or is there a repair MBR part of Ubuntu?

---

### Post by taurus on 2008-01-11
> **Xavieran said:**
> I installed Arch Linux on a separate partition to Ubuntu and now I can't access my Ubuntu partition...I get a GRUB error 13 Invalid or Unsupported file format...

The settings for Ubuntu in GRUB are:

[B][COLOR="Blue"]rootnoverify (hd0,0)
makeactive
chainloader +1
[/COLOR][/B]
What should I change?
Or is there a repair MBR part of Ubuntu?

That looks like an entry for windows, not Ubuntu!  Did you install GRUB when you installed Arch?

---

### Post by Cypher on 2008-01-11
A Linux entry in GRUB would resemble something like mine below..
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3a8a2f42-f953-4fb0-937
3-9f5f188c5b20 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

---

### Post by Xavieran on 2008-01-11
Yes I did install GRUB...I just had a flash of inspiration though!

I will copy the Ubuntu entry from hda0,0 and stick it in menu.lst in Arch

---

### Post by Xavieran on 2008-01-11
Sorry for wasting your time guys :(
I just copied ubuntu's section into arch's GRUB...
:)

---

### Post by Cypher on 2008-01-11
> **Xavieran said:**
> Yes I did install GRUB...I just had a flash of inspiration though!

I will copy the Ubuntu entry from hda0,0 and stick it in menu.lst in Arch

Bingo!

---

