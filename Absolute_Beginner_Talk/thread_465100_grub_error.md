---
title: "grub error"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-06-05
when i am installing ubuntu fiesty i get a grub install error no number at the end of the install not after restart like says can not load the grub on to hda "0"

---

### Post by arkham on 2007-06-06
grub has a slightly different way of referring to your hard drives etc. than linux does.  from it's perspective, the device with the bootbloc - the one you boot from and that it loads from - is (hd0)

If you boot off your first IDE drive - then this is equivalent to /dev/hda

it's "root" directory, i.e. where it expects to find your kernel.  I have my /boot mounted separately on the first partition of my hard disk.  To continue with the example from above, then Linux sees that as /dev/hda1 and grub sees it as (hd0,0)

So, the error message is saying that grub cannot install itself onto the device you have set up as your boot device - (hd0), and in the example above /dev/hda

There can be various reasons for this, one of the most common is an issue with drivers, such as the driver for your hard drive controller.  Common ones include sata_nv and ata_generic.  I recently had this problem because I was using an Nvidia RAID chipset and the driver was not loading.

Without more info it is difficult to say what your isu is, but hopefully the info will help anyway

---

### Post by metzy85 on 2007-06-07
well i have a dell laptop and i have one hard drive which 60gb i have 2 partitions  one is the main and the other 14 gb for my linux and i tried it again and i stil got the grub error

---

