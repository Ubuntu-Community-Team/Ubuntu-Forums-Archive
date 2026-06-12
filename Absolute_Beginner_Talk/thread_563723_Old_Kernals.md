---
title: "Old Kernals"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by AirAshby on 2007-09-30
Are the Kernals listed in the grub boot menu after upgrading Ubuntu actually physically on my hard drive? Or are they just links in the Grub Boot Menu File?

If they're still physically on my hard drive can I delete them? Or do I just edit them out of the Grub Boot Menu?

---

### Post by Pumalite on 2007-09-30
Not a good idea to delete them. It's better to have them for a rainy day (after an update gone wrong as an example), so you have something to boot from.

---

### Post by roy92 on 2007-09-30
you can try editing  /boot/grub/menu.lst   there is where they are writen all your kernels, you can delete them or edit them.



mine is this: (line 126 to 141)

title		Kubuntu
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=009c963e-143f-46df-aa7c-4ab4dcdad19b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=009c963e-143f-46df-aa7c-4ab4dcdad19b ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

#title		Ubuntu, memtest86+
#root		(hd1,1)
#kernel		/boot/memtest86+.bin
#quiet

first they were like 6 more things there, but i removed them and leave the necesary.

I hope this is what you are searching for

---

### Post by bapoumba on 2007-09-30
Editing /boot/grub/menu.lst may work until the next kernel upgrade, then the file is going to be automagically written over, and you'll have all the previous kernel entries back ;)

It is always better to keep the previous working kernel.
You can remove the other ones from synaptic (and they won't show up any longer).

---

### Post by mcduck on 2007-09-30
Just uninstall the linux-image packages of old kernel versions with Synaptic, and the entries in Grub will also be removed. You can also remove the kernel headers & restricted modules packages of those old kernel versions.

Anyway, after a kernel update it's a good idea to test the new kernel for some time before removing the old one, but when you are sure that the new kernel works fine on your machine it's safe to uninstall the old one. Some people like to one older kernel version always available, but I always remove them after running the new kernel version for a day or two.

I wouldn't recommend just editing the grub menu, as the kernel files are still wasting your disk space, and even if you wanted to use them it's not that easy if they are not in the menu ;)

---

### Post by nowshining on 2007-09-30
I suggest leaving them if u haven't removed them yet as some others have suggested for incase something does go wrong - :) plus it all depends on how many Gigs your Hard Drive has -  the more - the less important it is to remove them, and the less the more important it is to remove the older ones to make room for other more important things.

---

### Post by mcduck on 2007-09-30
There is absolutely no way you would even in the worst situations need more than one old kernel available. It's just useless to keep *all* old versions on your hard disk & grub menu.

Keep one old kernel if you want, remove the rest.

---

### Post by Gremlinzzz on 2007-09-30
you have 2 choices
sudo gedit /boot/grub/menu.lst
and comment it out by putting # in front of lines
synaptic package manager search for linux-image and remove old kernels
then sudo apt-get autoremove to clean up junk not being used.

---

### Post by nowshining on 2007-09-30
> **mcduck said:**
> There is absolutely no way you would even in the worst situations need more than one old kernel available. It's just useless to keep *all* old versions on your hard disk & grub menu.

Keep one old kernel if you want, remove the rest.

I agree with you mcduck on that - :) But keeping at least one good kernel like u said is good. Again tho make sure at least the first and the Old one your going to keep both work FINE with your current setup - reboot into the intended one to keep with your current setup to make absolutely sure it works.

---

