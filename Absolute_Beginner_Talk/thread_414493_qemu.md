---
title: "qemu"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by JamesA on 2007-04-19
Hey guys.

I have a question about qemu and what it can do.

I have one harddrive with ubuntu on it, the other with xp. Is it possible to run qemu on linux, and somehow make it run windows from the other hd?

Or do i actually have to install windows from inside linux?

CHeers

---

### Post by rufius on 2007-04-19
You can do that, you'll have to specify to qemu that the image you want to boot from is actually /dev/<whatever>. I forget the command but do some reading on qemu on google and you should find it.

---

### Post by madmetal on 2007-04-19
> **JamesA said:**
> Hey guys.

I have a question about qemu and what it can do.

I have one harddrive with ubuntu on it, the other with xp. Is it possible to run qemu on linux, and somehow make it run windows from the other hd?

Or do i actually have to install windows from inside linux?

CHeers

what do you actually want to do?
access the windows partition , run windows application or try windows on qemu?

---

### Post by igknighted on 2007-04-19
There are ways to trick these virtualization programs to use an existing drive, however you will run into all sorts of windows activation problems because they are two different sets of hardware you are trying to run on.  Therefor, installing a new version is the way to go.

---

### Post by Pobega on 2007-04-19
Let's call the external partition with Windows on it /dev/sdb, and let's say Windows is on the first partition.

```
qemu -boot c -hda /dev/sdb1
```

That should boot QEMU in /dev/sdb1. I've never used this before myself but it should work perfectly fine, but I warn you, QEMU is a little bit slow and sluggish, and although I **hate** recommending proprietary software, VMWare handles things a little bit better than QEMU.

---

### Post by JamesA on 2007-04-19
i want to run windows from inside linux, like in the following screenshot:

[http://kitty.in.th/files/376/qemu.png](http://kitty.in.th/files/376/qemu.png)


However, linux is on one hard drive, and windows is on another.

Im wondering weather or not you can make qemu point at another harddrive.

Thank you both for the quick replys

---

### Post by JamesA on 2007-04-19
woah thanks everyone. Very quick to reply (i think i'll come here more often ;))

Cheers Pobega, i'll look into it and keep you all updated on how i do.

:)

---

