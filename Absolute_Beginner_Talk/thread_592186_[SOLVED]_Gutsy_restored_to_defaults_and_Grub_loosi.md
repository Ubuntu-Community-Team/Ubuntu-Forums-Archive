---
title: "[SOLVED] Gutsy restored to defaults and Grub loosing settings"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by dooglex on 2007-10-26
Hi so ive just upgraded fiesty to gutsy and wanted the nice new interface and backgrounds and menu bars etc as well as wanting to remove emeerald etc that i had setup before and use the new desktop effects options instead, how do i do this? is there a way to restore the install to default? or do i have to do a clean install?

Also does grub have to revoke to defaults after every update? it means i loose my vista partition and have to restore a backup i made in a flash of logic when i orgonally got it to work.

Thanks

---

### Post by MegaJim on 2007-10-26
For some reason during upgrades the update-grub program ignores any non-linux partitions.

For this reason, its a good idea to put vista/xp boot stanzas after the #end automagic kernel list section of your /boot/grub/menu.lst

Heres an extract from mine to make it clear.

```
 ## ## End Default Options ##

#automatic kernel list created by update-grub goes here, itwill overwrite any existing stanzas

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu 7.10, kernel 2.6.22-14-generic (dev/hda5 | hd0,4)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3df4c21b-1b38-44eb-80fb-8efd2dcb1990 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Microsoft Windows XP Home (dev/hda0 | hd0,0)
root		(hd0,0)
makeactive
chainloader	+1

```

both those entries will stay there until manually removed.  Good thinking on keeping a backup, its always a good idea.  If you don't have one though, theres normally a backup located at /boot/grub/menu.lst~ (same file with a tilde on the end)

---

