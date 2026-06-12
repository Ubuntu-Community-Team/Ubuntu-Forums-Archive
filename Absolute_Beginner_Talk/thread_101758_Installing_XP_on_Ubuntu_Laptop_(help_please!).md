---
title: "Installing XP on Ubuntu Laptop (help please!)"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by hobnobsandtea on 2005-12-10
I have a 5gb partition left behind for windows xp. 

But how do i install XP on that partition?

I thought I would just put the CD into the drive and it would boot, but it doesnt, even though primary boot device is CD. So i thought I could somehow use GRUB to install XP on the 5gb partition.

ALL HELP IS NEEDED !!

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=hobnobsandtea]I have a 5gb partition left behind for windows xp. 

But how do i install XP on that partition?

I thought I would just put the CD into the drive and it would boot, but it doesnt, even though primary boot device is CD. So i thought I could somehow use GRUB to install XP on the 5gb partition.

ALL HELP IS NEEDED !![/QUOTE]
If the primary boot device is the CD, and you have a CD in the drive, it should boot to the installer regardless of what's on the hard disk.  If you disable the hard drive in the BIOS, will it boot then?  Have you used this CD before?  Could be that it got scratched up or something...

---

### Post by Rackerz on 2005-12-10
Is it a bootable XP cd?

---

### Post by BoyOfDestiny on 2005-12-10
Hi, as far as I know (ex-windows user here), all XP install discs are bootable. 
However, I believe Windows needs to be installed on the first partition of a drive, and it overrides grub. Usually people install windows first, then put linux on top, since GRUB plays nice with the other OS's on the drive... 

Anyway, hope this helps you.

---

### Post by Rackerz on 2005-12-10
[QUOTE=BoyOfDestiny]Hi, as far as I know (ex-windows user here), all XP install discs are bootable. 
However, I believe Windows needs to be installed on the first partition of a drive, and it overrides grub. Usually people install windows first, then put linux on top, since GRUB plays nice with the other OS's on the drive... 

Anyway, hope this helps you.[/QUOTE]

Yeah that's true. Windows will overwrite GRUB and wont play nice with other OS's.

---

### Post by nubuntux on 2005-12-11
hi, i think windows os does not allow to install first any linux os on the first parition of memory boot record.... it must be windows then linux...

---

### Post by hobnobsandtea on 2005-12-11
ok that may be so but how do I get out of this jam now.

I cant boot any cd!

---

### Post by Flawlessly on 2005-12-11
[QUOTE=nubuntux]hi, i think windows os does not allow to install first any linux os on the first parition of memory boot record.... it must be windows then linux...[/QUOTE]
:KS What he/she said.:KS

---

