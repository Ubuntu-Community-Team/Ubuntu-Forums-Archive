---
title: "Grub...How do you edit it?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by ravosava on 2007-09-03
Hi, I know people have already asked this questions, but the questions they asked aren't really helpful.
I would like to know how to comment out the other kernel options so I only have the most recent release, the recovery mode, and windows as options. Also, a friend of mine mentioned you could change the color of grub, and I was wondering how to do this as well. 
I would like to thank those of you who take the time to read and answer this post, it is much appreciated...or will be at least. :)

---

### Post by taurus on 2007-09-03
Edit /boot/grub/menu.lst with

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
And if you want to comment out something in there, just place a # in front of it.

---

### Post by overdrank on 2007-09-03
> **ravosava said:**
> Hi, I know people have already asked this questions, but the questions they asked aren't really helpful.
I would like to know how to comment out the other kernel options so I only have the most recent release, the recovery mode, and windows as options. Also, a friend of mine mentioned you could change the color of grub, and I was wondering how to do this as well. 
I would like to thank those of you who take the time to read and answer this post, it is much appreciated...or will be at least. :)

Hi and maybe this link will help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by thelocust on 2007-09-03
You can just edit menu.list to make it say whatever you want. make sure you back it up before you mess with it and also I print out a copy of mine so that I can manually boot it if stuff gets really messed up. I attached a copy of mine as an example. Also every time your kernel upgrades it overwrites your menu.list so again back it up.

```

title        Kubuntu Feisty
root        (hd0,0)
kernel        /vmlinuz-2.6.20-16-generic root=UUID=f27ad5b3-644a-41d0-96db-9b29566eaf2a ro quiet splash
initrd        /initrd.img-2.6.20-16-generic
quiet
savedefault

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

title        Recovery Mode
root        (hd0,0)
kernel        /vmlinuz-2.6.20-16-generic root=UUID=f27ad5b3-644a-41d0-96db-9b29566eaf2a ro single
initrd        /initrd.img-2.6.20-16-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /memtest86+.bin
quiet

```

---

### Post by ravosava on 2007-09-03
Thanks again everyone...:)

---

