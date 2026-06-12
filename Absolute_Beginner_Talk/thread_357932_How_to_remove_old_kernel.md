---
title: "How to remove old kernel?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-10
I just updated to the 2.6.17.11 kernel, now I have both 17.10 and 17.11 on my system. How can I remove the older kernel (2.6.7.10) without breaking anything.

---

### Post by JayTee on 2007-02-10
Easiest way would be to type Alt-F2 and run GKSU NAUTILUS, that'll give you the Nautilus File Manager with root priviledge, then navigate to the /boot folder and you'll see the kernel files for both 17-10 and 17-11. Be very, very careful not to delete the 17-11 files when you delete the 17-10 files. 
files to delete:
 config-2.6.17-10-generic
initrd.img-2.6.17-10-generic
System.map-2.6.17-10-generic
abi-2.6.17-10-generic
vmlinuz-2.6.17-10-generic

after you delete those files you can also edit your GRUB menu list for boot by editing the 
/boot/grub/menu.lst file and removing the entries that reference the older kernel.

---

### Post by spoot on 2007-02-10
I was about to ask the same thing, after the kernel update of yesterday there are now two possible kernels in my GRUB menu. Since the new one works fine I'd like the "clean" way to remove the old one. Can it be done with Synaptic alone, if so, what packages and will GRUB automatically be updated?

---

### Post by konst88 on 2007-02-10
This is exactly the opposite from the easy way..
The easy way is to remove the lernel using synaptic, or any other package manager.
Just search for the word linux in the name of the packages.

---

### Post by mcduck on 2007-02-10
> **spoot said:**
> I was about to ask the same thing, after the kernel update of yesterday there are now two possible kernels in my GRUB menu. Since the new one works fine I'd like the "clean" way to remove the old one. Can it be done with Synaptic alone, if so, what packages and will GRUB automatically be updated?
Yes, you can just search & uninstall the old kernel packages with Synaptic (or apt-get). This will also remove their entries from Grub menu. (tip: searh for word 'linux' in package names only)

---

### Post by bapoumba on 2007-02-10
In addition to previous post, I would say always keep one older kernel that works. It's not ubuntu-specific recommendation ;)
You can then boot on this old-but-functional kernel if anything happens.

---

