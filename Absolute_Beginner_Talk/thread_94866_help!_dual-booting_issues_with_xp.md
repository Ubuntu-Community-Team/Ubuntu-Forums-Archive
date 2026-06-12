---
title: "help! dual-booting issues with xp"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-11-25
hi, i'm running xp pro sp2 on my pc, and whenever i try to install ubuntu onto a hard drive, it renders my xp unbootable. any ideas on how to fix this? I figure it has something to do with having to reformat the hard drive, but the one I am trying to use is already wiped.

Oh by the way, it tells me that my NTFS file is missing.
I'm aware that there are threads similar to this, but I'm not really advanced enough to understand most of it, so a simpler, plain-english explanation would be really helpful

---

### Post by tomski on 2005-11-25
you need to edit the following file menu.list
this lives in a directory called /boot/grub
to edit open a terminal and type:

sudo gedit /boot/grub/menu.lst

you need to add :

title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

cut/paste that in the section below were your kernel is listed

then save the file and then close gedit and pass this in the terminal:
sudo grub-install /dev/hda

then reboot 

et voila

should be ok

---

