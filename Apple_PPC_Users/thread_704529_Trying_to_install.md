---
title: "Trying to install"
date: 2008-02-22
forum: Apple PPC Users
---

### Post by Haffi112 on 2008-02-22
Ok I'm kind of a newb to this Linux world but I want to try it and I'm in a kind of trouble.

I have a two year old 12" PPC I want to boot with Kubuntu but the CD drive is broken and the disk utility isn't installed so I can't format the hard disk.

So I have to install it some other way, I have a portable hard drive I could install from but I don't know how.

Any tips?

(I excuse for my newbness, it will wear off soon (I hope))

---

### Post by sandysandy on 2008-02-22
do you have kubuntu !

---

### Post by Haffi112 on 2008-02-22
Yes I just downloaded kubuntu-7.10-desktop-powerpc today. Will that work?

---

### Post by stream303 on 2008-02-22
Only two years old and the drive is broken?  Maybe so, but have you tried booting with the "C" key held down?  Is the iso burned as an iso image and not just copied over, and burned at a speed your cdrom can accept?

Just crossing my fingers that the cd drive isn't really broken. :)

If it is truly gone, can you beg, borrow, or buy an external firewire cd/dvd drive?

If so, you can get it to boot by powering up into open-firmware by holding down (command-option-o-f), and issuing:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

Dont' confuse command (cloverleaf) with ctrl.

---

