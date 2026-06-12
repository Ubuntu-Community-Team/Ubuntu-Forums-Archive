---
title: "[SOLVED] How to change the disk that grub boots from?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-12-25
I have a system that's ended up a little oddly configured.  There are 3 hard disk drives, 
one 15GB IDE (hda), 
one 80 GB sata(sda), and 
one 250GB sata (sdb)

The grub device.map is

```
(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb
```

The root of my gutsy install is on sda, and sdb is just a data drive.  I used to have feisty installed on the IDE drive hda before I clean installed gutsy to the system

I tried removing the IDE drive physically, and the system will no longer boot.  I also tried using Super Grub disk to make it boot while the IDE was removed, but even though it finds the grub menu on sda, when it tries to boot, I get a file not found error.

So, I put hda back in, and the system runs/boots normally again.  The main entru in menu.lst that I use to boot is

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=54a56495-0f06-4d8e-9739-6f2353cfe58d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

but I am at a loss as to what is preventing it booting without the IDE drive.  Can anyone help me to make it boot without the hda (hd0) drive please?

---

### Post by Capricori on 2007-12-25
I'm just guessing, but if you remove the IDE drive (hd0), surely the drive with GRUB on it (hd1) would move to (hd0)?
Perhaps changing menu.lst to reflect that would solve the problem?

It's just a suggestion, I wouldn't jump straight in and do it, cos if I'm wrong, you're system could be even more unbootable :S

---

### Post by ubnewbie2 on 2007-12-25
> **Capricori said:**
> I'm just guessing, but if you remove the IDE drive (hd0), surely the drive with GRUB on it (hd1) would move to (hd0)?
Perhaps changing menu.lst to reflect that would solve the problem?

It's just a suggestion, I wouldn't jump straight in and do it, cos if I'm wrong, you're system could be even more unbootable :S

Yes that makes sense.  Maybe I can try it by editing that line 'on the fly' using super grub disk.

---

### Post by ubnewbie2 on 2007-12-25
Worked!  thanks - marking this is solved

---

