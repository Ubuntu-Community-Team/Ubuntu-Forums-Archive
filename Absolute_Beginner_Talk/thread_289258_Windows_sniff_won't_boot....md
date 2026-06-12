---
title: "Windows *sniff* won't boot..."
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2006-10-30
Okay, so everything has been hunky dory for about 3 months, I think, with my computer.

I have dual boot with XP and Ubuntu, usually using Ubuntu.

Well, I tried to boot into XP tonight, which usually works, and it didn't work.  This happened once before, but rebooting fixed it.  Here's the error:
```

Booting 'Windows XP Professional'

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```

I need to use Windows right now.  Can anyone tell me what the hell I need to do?  

And another thing, when I gave up just now, and booted Linux, my panel (dock thingy) was in the middle of the screen, and wasn't obeying my orders, and all the dividers got moved to the right end.  But that's not a big problem.

J

---

### Post by ciscosurfer on 2006-10-30
[This page should help]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").  Also, you can try searching 'grub' on the wiki as well as take a look at my link to GRUB in my signature.

---

### Post by SunnyRabbiera on 2006-10-30
Grub sometimes does this, though rare.
But maybe it is good riddance eh? :P

---

### Post by chameleon_789 on 2006-10-30
You could try **sudo update-grub** in a terminal maybe? I think that redetects file systems, rebuilds the grub menu.lst etc.

---

### Post by ciscosurfer on 2006-10-30
> **chameleon_789 said:**
> You could try **sudo update-grub** in a terminal maybe? I think that redetects file systems, rebuilds the grub menu.lst etc.

Not exactly.  To detect where and what your filesystem/partitions are and where they are located, you need to issue```
sudo fdisk -l
```For a complete (at least semi-complete) explanation of what **update-grub** accomplishes, read the man pages```
man update-grub
```The **update-grub** command essentially looks in your /boot directory and writes (or rewrites) your /boot/grub/menu.lst file.
On the other hand, grub-install will GRUB images into the DIR/boot directory specfied by --root-directory, and uses the grub shell to install grub into the boot sector.  To issue this command```
sudo grub-install
```It is wise to read up on the is command as well before using it: **man grub-install**

---

