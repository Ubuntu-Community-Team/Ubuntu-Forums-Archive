---
title: "Installing UBUNBTU on USB hard drive"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Cicrano on 2007-09-13
It's been a couple of weeks in browsing these and other linux forums, googling and despairing but I finally made it!

Stupid little details that are not mentioned or at least not easily findable anywhere!

The first and most important detail:

In the Advanced tab in the last pre-install summary one must say to install bootloader in hd1 -- the USB drive. Because: 
--- not good to mess around with the MBR of the laptop hard drive!
--- if you're somewhere else out of home why complicate things with hardware that's not present?...

UBUNTU and GRUB do NOT necessarily call the hard drives the same thing!

In UBUNTU my USB drive is called as SDA1 -- SCSSI0 -- hd1 (the laptop hard drive being hd0)

GRUB thinks otherwise! He calls the USB drive hd0 and the laptop hard drive hd1
(as a geometry command at the grub prompt will show)

So... after an innocent normal install... Error 17   :frown:

Here are the details to make things work:

You can't right after install edit the menu.lst...

Solution -- boot Puppy live cd, mount and enter sda1, edit the boot/grub/menu.lst
and change the hd designations for linux and windows from 1 to 0 and from 0 to 1
also add acpi=off to the kernel line!
Even though it has been a boot parameter to the live CD, UBUNTU ignores this when installing to hard drives! -- BUG!
KURUMIN remembers the boot parameters from the live CD -- more intelligent!

Then you do the first boot direct from the USB drive and everything goes well.

But then you update...
And stupid UBUNTU puts everything wrong again!

So boot from Puppy and repeat the process!

Hope this saves a lot of time to other newbies!

:lolflag:

---

### Post by marx2k on 2007-09-13
I am writing this on a computer on which I booted from an external USB drive with Ubuntu on it.

The solution for me with the mucking with menu.lst all the time was changing menu.lst option:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

```

Don't remember what it was before.

Also, this is how the chainloader looks...
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=37b3c170-6b27-471b-a32d-60bd8b412041 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

So thats probably how you want it to look. (change the UUID to your UUID or to your physical drive (/dev/sdb1)

---

