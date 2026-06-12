---
title: "Cannot Boot Lubuntu on Zenbook UX32A"
date: 2013-03-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by KarateCowboy on 2013-03-02
Hello Friends,

I installed Lubuntu on a new UX32A Zenbook. Everything went successful but when I reboot it goes straight to the BIOS. 

When I look in the BIOS it appears that I deleted any entries from the UEFI boot options.  This was from a prior attempt to install arch linux.

Does what to add to the boot options to get lubuntu installed?

My UEFI system partition was on /dev/sda1 and my Lubuntu installed to /dev/sda6

The laptop came pre-loaded with Windows 7. I cannot boot into that either.

My bios version is UX32A.206 

I am writing this on that laptop, running the Lubuntu Precise x86_64 live disk.

---

### Post by KarateCowboy on 2013-03-02
I solved it.

The UEFI System partition was labeled bios-grub rather than boot. That is why when I ran boot-repair it would not correct the problem.

I used gparted and reformatted /dev/sda1 to have the boot flag.  Then ran boot-repair again. 

Now I am running ubuntu from the machine install.

---

