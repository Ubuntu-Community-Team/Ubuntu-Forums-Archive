---
title: "Ubuntu install wiped my minimac hard drive!"
date: 2007-01-28
forum: Apple PPC Users
---

### Post by Powercat on 2007-01-28
I was trying to install ubuntu on my mac mini ppc. I partition a swap and a ext3, and I had my hfs+, then I get an error about something about apple_bootstrap HFS partition, so I make a hfs partition but it still doesn't go through.
So then I notice this 50kb partition that was unknown. I click on it and set it to bootable and BANG my whole hard drive was erased.

Any chance of recovery?

---

### Post by meng on 2007-01-28
Sounds fishy. How do you know it was erased? The partition manager shouldn't actually institute any changes to the disk until you confirm. (At least that's how it works on a PC.)

---

### Post by Powercat on 2007-01-28
The OS doesn't boot. Going back to gparted shows all empty space and the MAC OSX install CD shows no partition either.
It's all gone.

---

### Post by meng on 2007-01-28
Okay, that certainly looks bad. Which version of Ubuntu were you using?

---

### Post by samden on 2007-01-31
I recognise that error about the Apple_Bootstrap partition.

When you are partitioning the disk as you install ubuntu, manually edit the name of the boot partition, and call it Apple_Bootstrap. I had to do this when installing - don't ask me why!

It doesn't sound healthy for your hard drive, you probably selected "erase entire hard drive" or something during the installation process accidentally. I hope you backed up and have your OSX installation disks! If you do, no worries - may be better to start from a clean system anyway.

---

