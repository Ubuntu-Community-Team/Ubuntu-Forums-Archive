---
title: "Dual Booting"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by evandec on 2006-06-17
I want to insall another OS on a hard drive that already has ubuntu on it. Is that a program I should use to set up dual booting?

---

### Post by darkali on 2006-06-17
Since you didn't specify, I will assume you want to install Windows XP.
Do not install other distro (fedora,suse) on the same partition ubuntu is. Otherwise it will break ubuntu.

Boot from the Ubuntu CD.
Start Gparted.
Applications -> System Tools -> GParted

You need to resize your partitions so to accommodate the other OS, this will depend on your hardware. You also need to set the filesystem of your new partition to NTFS.

Now install windows.
When it's installed completely (after a few reboots) do this: 

1. Boot-up computer into Ubuntu Installation CD
2. At "boot:" prompt, add "rescue" to the argument (boot: rescue)
3. Follow the instructions on screen

Now assumed that /dev/hda is the location of /boot partition of ubuntu, type this in the terminal.

```
grub-install /dev/hda
```

This will install Grub and make entries to both OSes, so when you boot you choose the one you want.

---

