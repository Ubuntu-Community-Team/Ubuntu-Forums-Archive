---
title: "Where is the boot-loader?? Please help."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-28
Hi all,
I have installed ubuntu..and now want to dual-boot it with fedora..
I have installed fedora on a new partition...but theres no option to boot into fedora in grub..
Do i install the boot-loader in the partition where fedoras root is there?? or in the MBR?
Please help me...
thanks

---

### Post by Zelut on 2006-07-28
The boot loader is generally loaded on the MBR.  At least that is where I always put it.

What I would try is running 'sudo grub-install /dev/hda' (or the location of your primary drive).  Grub *should* find the Fedora install and auto-add that.  If not you'll need to manually add the locations in the list

Give it a try & let me know, we can move to the next step if you need.

---

### Post by steve.horsley on 2006-07-28
I don't know what bootloader Fedora uses. Neither do I know where Fedora would have placed that bootloader. 

But GRUB is normally placed on the MBR (first sector) of the first hard disk. It then consults the file /boot/grub/menu.lst - that's the file you need to edit. 

Since Fedora didn't overwrite the MBR, maybe it put its bootloader at the start of its own root partition wherever that is. If that's the case, you should be able to chainload the Fedora partition. The stanza for Grub would look like this:
> title          Fedora
root           (hd1,4)
chainloader    +1

---

