---
title: "uninstalling ubuntu"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by rdz on 2005-05-23
hello, I am using two operating systems on one hard disk (windows xp/ ubuntu 5.04). I installed linux boot loader (GRUB) on MBR. if I format ubuntu´s partitions, will windows xp boot? is there a way to restore windows xp boot loader?

---

### Post by tread on 2005-05-24
If you want to remove grub, you need to use the windows xp cd, boot off it and (do something I dont remember :) .. possibly fdisk/mbr) Google it .. you will remove quite a few hits for removing grub.

But even if you keep grub it should still boot to windows, and you can just reduce the timeout in grub options. (this in case you dont have the windows cd)

---

### Post by the_clown on 2005-05-24
I think the command is  fixmbr
Look at this site:
[http://tinyurl.com/2cg2u](http://tinyurl.com/2cg2u)

---

### Post by Mez on 2005-05-24
yes.

If you want to format the partition where GRUB is located, you need ANY windows XP Disk.

Put this in your computer and boot off it.

When you ge to a blue screen - it should give you the option to press "r" for a recovery conole.

do this, and then type "fixmbr" (without the quotes) at the prompt to overwrite the grub loader with the default Windows XP boot loader. Then, take out the CD, reboot and you have your old bootloader back,

---

### Post by rdz on 2005-05-29
it worked. thank you

---

