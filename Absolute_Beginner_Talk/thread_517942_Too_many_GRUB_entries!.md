---
title: "Too many GRUB entries!"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2007-08-05
I have double Ubuntu entries in my GRUB boot menu (plus an XP one.) How do I remove these as they appeared when I reinstalled Ubuntu.:confused:

---

### Post by carloslosgrande on 2007-08-05
[FONT="Comic Sans MS"]I assume you mean the kernel entries, when the kernel is updated the default is to keep the last kernel in case there is some problem and you can then go back to it.
Otherwise you can go into SynapticPackageManager and find the kernel you think is excess (probably version 15) and remove it.[/FONT]

---

### Post by Steve1961 on 2007-08-05
You can edit the grub menu by typing:

sudo gedit /boot/grub/menu.lst

Be careful though.  Only remove entries if you are absolutely sure they are duplicates and not just entries for single-user mode and different kernels.

---

### Post by cwmoser on 2007-08-05
Determine which partition the Grub boot is point to.  Then edit the file /boot/grub/menu.lst removing the ones you don't want to show in the boot menu.

You might need to do a little detective work locating *which* partition grub looks to for the /boot/grub/menu.lst file.  I have 3 instances of Ubuntu in 3 different partitions.  I mounted each partition and edited each /boot/grub/menu.lst file  inserting the name of the partition in an appropriate menu text so I would know *where* grub was looking for the /boot/grub/menu.lst.  

When I found the proper /boot/grub/menu.lst, I edited the file removing entries I no longer wanted to appear at boot up.

Carl

---

### Post by ron999 on 2007-08-05
If you edit the GRUB menu list you can just put hash symbols in front of the lines you don't need.
Then save it.
Then if you screw up you can just go back and remove the hash symbols.

Like this:-
#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a07b615d-3f3d-4125-92ed-e9135be51175 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

---

### Post by fraser_m on 2007-08-05
I have commented them out with #s. With that work?

---

### Post by ron999 on 2007-08-05
> **fraser_m said:**
> I have commented them out with #s. With that work?

If you're sure that you've hashed the correct ones and you save it then it should work.
The lines I posted are copied from my menu.lst.
It works for me.

---

### Post by fraser_m on 2007-08-05
Done.

I've also set it not to show the menu unless I press ESC within 1sec!

---

### Post by ron999 on 2007-08-05
> **fraser_m said:**
> Done.

I've also set it not to show the menu unless I press ESC within 1sec!
 
Wow, you'll have to be quick on the draw!:lolflag:

---

