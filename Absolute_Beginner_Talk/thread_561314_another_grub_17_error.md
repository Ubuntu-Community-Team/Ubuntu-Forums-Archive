---
title: "another grub 17 error"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by marduuk on 2007-09-27
ok lets start with the fact that i have ubuntu loaded on hd1... full drive install
hd0 is a 120gb ntfs disk
sd0 is a winxp drive

supergrub disk does work for booting but doesnt fix the problem when i use the fix feature
i can also boot lin from the live cds "boot first hdd" option

i have checked and the menu.lst file seems to be correct but ill pastebin some stuff and link it below.

heres the boot area of menu.lst ....... [http://paste.ubuntu-nl.org/38782/](http://paste.ubuntu-nl.org/38782/)
[http://paste.ubuntu-nl.org/38785/](http://paste.ubuntu-nl.org/38785/)

heres full menu.lst .... [http://paste.ubuntu-nl.org/38787/](http://paste.ubuntu-nl.org/38787/)

any help is appreciated... TIA aaron

---

### Post by Arwen on 2007-09-27
(hd1,0)  ?? Your first disc shouldn't be hd0?Also did you try twice to install ubuntu,one 32bit and one 64bit?Cause your fstab looks like mine,when I did such thing..
{Ubuntu, kernel 2.6.20-15-generic} and {Ubuntu, kernel 2.6.20-16-generic}

---

### Post by logos34 on 2007-09-27
If this is the Bios hard disk boot order:

1. 120 GB ntfs disk ---> /dev/hda (hd0)
2. 160 GB ubuntu   ---> /dev/hdb (hd1)
3. 80 GB ntfs          ---> /dev/sda (hd2)

(at least that's what it appeared to be when you installed) then Grub should be on the mbr of hda.  Maybe when you try to fix it with supergrub it's writing to a different disk.  Try reinstalling Grub but make sure it goes on **(hd0)**.  UIse this [howto]("http://ubuntuforums.org/showthread.php?t=224351") but enter '**setup (hd0)**'.

---

