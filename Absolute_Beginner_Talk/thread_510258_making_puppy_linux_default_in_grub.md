---
title: "making puppy linux default in grub?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by blk03mitsues on 2007-07-26
I've already read the threads about making an OS the default OS in grub but it aint working for me for some reason.

I just installed Puppy Linux and it configured GRUB on it's own. but everytime the computer boots i get a little menu that ask to either boot from linux, install grub to floppy or install grub to HD. i'm trying to get grub to automatically load puppy linux on each boot/reboot

GNU GRUB V 0.97

#start grub global section
#timeout 30
color light-grey/blue black/light-gray
#end grub global section
#linux bootable partition config begins
title linux (on/dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz root=/devhda1 ro vga=normal
#linux bootable partition config ends


then it's got the code and everything for the install to floppy or hd stuff.

---

### Post by Pragmatist on 2007-07-26
Please post your **/boot/grub/menu.lst **

---

### Post by blk03mitsues on 2007-07-26
the PC i have the grub problem isnt hooked up to the net so i really cant post it. but let me try to ask a different questions....

i guess this is the import stuff about grub right?

title linux (on/dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz root=/devhda1 ro vga=normal


what do i need before and after this code?

---

### Post by Pragmatist on 2007-07-26
There is tons of information on the puppylinux website:
[http://puppylinux.org/wikka/HardDiskInstall](http://puppylinux.org/wikka/HardDiskInstall)

Or,
[http://puppylinux.org/wikka/TextSearch?phrase=grub](http://puppylinux.org/wikka/TextSearch?phrase=grub)
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

---

