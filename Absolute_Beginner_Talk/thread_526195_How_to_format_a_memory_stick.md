---
title: "How to format a memory stick"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by MacMagnus on 2007-08-15
I'm an Ubunty-user (Feisty), and have a Verbatim Store'n'Go memory stick (I think it's the latest version) that I can't use in Linux (at least Ubuntu).

It works to mount the unit, and also read and write files to it.

But it's a problem with the storage capacity. It's original size is 520 MB. But due to a mechanism that makes you able to password-protect a second partition of the stick, I now have only about 47 MB; thats because the remaining bytes are "locked up" in the "Privacy Zone".

I don't think Verbatim have released any Linux-drivers for this stick. So the remaining space is unavailable.

What I'm wondering about is if there's some way to just delete EVERYTHING that's on that stick, just make it a regular flash-drive.

I've tried cfdisk, but it won't work because the stick is read-only.

Any clues?

---

### Post by shad0w_walker on 2007-08-15
You should be able to to use gparted to just delete the partition and replace it. If the drive is write protected there may be a switch on the side to set it to read/write.

---

### Post by Outrunner on 2007-08-15
You can't format a drive while it is mounted. Boot into your Ubuntu LiveCD and search  for "Gnome Partition Editor" in the menus and go on from there.

---

### Post by shad0w_walker on 2007-08-15
Its a memory stick, you can unmount it in gparted with out needing to run from a live cd. The only time you need to run from a live cd is if your messing with your root filesystem.

---

### Post by MacMagnus on 2007-08-15
I started gparted, but it only showed a volume of about 47 MB. Funny, because it reads 520 on the outside of the stick...

There's no button on the outside either, who possible could do some magic.

I think there's some firmware on it, that causes me to not access the full volume.

---

