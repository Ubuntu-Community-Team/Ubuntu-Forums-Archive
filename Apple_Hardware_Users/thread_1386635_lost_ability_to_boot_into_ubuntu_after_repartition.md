---
title: "lost ability to boot into ubuntu after repartition"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by clem75 on 2010-01-20
I wanted to update to the latest ubuntu but was short a couple of gigs in my linux partition. So i created a Gparted Live bootdisk and repartitioned my hard drive: i took 5 gigs from my mac os partition and moved it to the linux partition...

After that i could no longer see any boot option aside from Mac OS when starting the computer with the option key held down. So i thought maybe rEFIt might be the solution (i have no idea what i'm doing really) and installed refit. I'm not sure what that achieved - i can still only see one boot option (mac os - although it's now named 'refit'...)

Could someone please help me revive my linux partition and possibly rename my Mac OS boot volume as 'mac os' in the bootloader screen.

I'm wondering if this has anything to do with grub but am afraid to cause further damage.

Cheers!

Clém

---

### Post by linuxopjemac on 2010-01-21
I would reinstall Grub first and then sync the partition tables. From the live CD, go to a shell and perform the following:

```
grub-install /dev/sda
```

(sda is your hard drive containing Linux, check that)

Then boot into rEFIt and sync the partition table with the Partition tool.

---

