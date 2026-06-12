---
title: "installing when I don't have a cd drive"
date: 2008-03-15
forum: Apple PPC Users
---

### Post by tamedcynic on 2008-03-15
I'm not sure if this shoudl go in installation and upgrades instead.  I chose this category, because the computers are ppc's. But here is my problem:

I work at a school and I have set up my own computer lab in my classroom and two other labs for other teachers.  We have hundreds of old iMacs that run really well on xubuntu.  However, there are some with broken cd drives.  Is there a way I can download it and do a hard drive installation? Or is it possible to use a USB flash drive to install it to a hard drive and go from there?

---

### Post by stream303 on 2008-03-15
Broken cd drives seem to be dying all over lately. :)

If you can get your hands on an external firewire cd drive, (I use a Memorex drive), you should be able to boot it at the openfirmware prompt:

Hold down CMD(cloverleaf)-Opt-O-F and power up.

At the openfirmware prompt:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

---

### Post by tamedcynic on 2008-03-16
Thanks! I tried it and it worked.  I'm really excited about this.  I set up a computer lab at the beginning of this school year and now all eight social studies teachers will have labs soon. The crazy part is that when we are all finished it will cost less than the software alone that they put on the computer lab in the library.

---

### Post by stream303 on 2008-03-16
My pleasure.  I gave you the wrong key combination in the post, so I got that corrected.  It hit me in the middle of the night. :)

Glad to hear that those machines still have some life left in them!

---

