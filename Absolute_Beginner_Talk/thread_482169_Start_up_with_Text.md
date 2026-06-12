---
title: "Start up with Text"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-06-23
When I start Ubuntu up I get a progress bar.  How do I set it so it will give me the text of what it is doing; showing me what drivers it is loading and such?

---

### Post by molly_001 on 2007-06-23
remove the "-quiet" tag from the appropriate ext3 partition boot loader line, in your menu.lst file.

Commands:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
dd if=/dev/hdx of=MBR-backup bs=512 count=1

The above two simply make a backup copy of grub and your mbr - always a good idea.

Then:

sudo gedit /boot/grub/menu.lst


and go in there and do what I wrote above.  Save.  Reboot.

---

### Post by louieb on 2007-06-23
to do it temporally when the grub menu come up press e to edit the entry. highlite the kernel line press e to edit remove the quite splash and press enter. then press b to boot. 
to make it permanent you'll have to edit your /bbot/grub/menu.lst

---

