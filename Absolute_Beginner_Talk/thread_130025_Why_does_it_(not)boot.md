---
title: "Why does it (not)boot?"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Pavel Kraynov on 2006-02-15
Hello, All! 

I try to install Ubuntu 5.04 on my workstation.
This PC has 3  HDD - 
Windows XP - on master on primary IDE controller
Fat32  HDD with files - on primary/slave
Ubuntu - secondary/master

After this "curvehands[-( " install i didn't saw the GRUB menu! NT loader boot XP as usual.
I have to install ubuntu, and set up in BIOS boot order from secondary/master

Now i saw grub menu, but couldn't load anything.

```

=== 
title Ubuntu vmlinuz-2.6.10-5-386 
root** (hd2,0)** 
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/**hdc1** ro quiet splash 
initrd /boot/initrd.img-2.6.10-5-386 
savedefault 
boot 
=== 

```

After some expieriements with option "root" and press [TAB] key I rewrote this section
```

=== 
title Ubuntu vmlinuz-2.6.10-5-386 
root **(hd0,0) **
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/**hdc1** ro quiet splash 
initrd /boot/initrd.img-2.6.10-5-386 
savedefault 
boot 
=== 

```

And enjoy Ubuntu!...

Why this \\:D/  had booted?
as I read in manual for Grub [http://www.gnu.org/software/grub/manual](http://www.gnu.org/software/grub/manual) 
option of root > Set the current *root device *to the device *device* and how this section root **(hd0,0) ** refer with this 
root=/dev/**hdc1**  ?:-k 


and the last....
i couldn't load XP system by GRUB!

Look for this section in menu.lst

```
=== 
title windows 
rootnoverify (hd0,0) 
chainloader +1 
=== 
```

This section code was automatically written by while ubuntu installed.
When I choose this section in grub menu the system hanging up. And "nothing else matters" :evil: 

It doesn't  work properly (as I read on this forum and in faqs)

where's the error?:confused: 
BR, Pavel.
ps I m just a newbie in linux and english too, excuse me :cool:

---

### Post by lha on 2006-02-15
Grub sees partitions numbered by their boot order. If bios is set to boot from hdc, then hdc will be seen as hd0. Please find a line with '#groot (hd2) and replace it with '#groot (hd0)' to make sure you are able to boot linux after a kernel upgrade.

To boot Windows, replace
title windows 
rootnoverify (hd0,0) 
chainloader +1 

with
title windows 
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0) 
chainloader +1

---

### Post by Pavel Kraynov on 2006-02-15
Thanks a lot. I'll try this option tonight ^)

What's the difference between **root** and **groot** ?

---

### Post by lha on 2006-02-15
[QUOTE=Pavel Kraynov]Thanks a lot. I'll try this option tonight ^)

What's the difference between **root** and **groot** ?[/QUOTE]
Whoops, I should have written 'replace #groot (hd2,0) with #groot (hd0,0)'.

When you do a kernel upgrade, a script called update-grub is run. It look for that option #groot and uses its parameter when creating new entries to replace the older ones. If you don't change groot, you'll have eventually end up with 'root (hd2,0)' instead of 'root (hd0,0)' in those Ubuntu entries.

See 
```
man update-grub
``` for more info

---

### Post by Pavel Kraynov on 2006-02-15
**Thanks, lha!**
I read tons of threads, but some was incomprehensible, some occult, some very strange. I understood thats years of siting in front of Windows ease off my brains but .... give me a chance. I try to understand!!!:-# 

There's some problems happened tonight when i try to play with grub config. (in previous). And I remember some while reading this post [http://ubuntuforums.org/showpost.php?p=733325&postcount=16](http://ubuntuforums.org/showpost.php?p=733325&postcount=16)
This newbie has a similiar problems...

grub does not recognized my ntfs partition while booting.[-( 

[FONT="Courier New"]grub/menu.lst[/FONT]

```
=== 
title windows 
rootnoverify (hd2,0) 
chainloader +1 
=== 

```
> "Unknown file system 0x7"

here is my [FONT="Courier New"][SIZE="2"]fdisk -l[/SIZE][/FONT]  (as i remember):rolleyes: 

```
device         boot system   OS
dev/hda1      *      NTFS     XP
dev/hda4              NTFS
dev/hda5              NTFS

dev/hdb1      *      FAT32   none

dev/hda1      *      ext3      ubuntu
dev/hda5              swap
```
Could anyone give me a link?

---

### Post by Pavel Kraynov on 2006-02-15
```
man update-grub
``` 

No update-grub on live cd.
How could I see just man pages w/o install grub package?

---

### Post by carlosqueso on 2006-02-15
[http://manpages.debian.net/cgi-bin/display_man.cgi?id=28cbab52197c2d63fef235673cb493d3&format=html](http://manpages.debian.net/cgi-bin/display_man.cgi?id=28cbab52197c2d63fef235673cb493d3&format=html)

Here it is.

---

### Post by lha on 2006-02-15
[QUOTE=Pavel Kraynov]**Thanks, lha!**
There's some problems happened tonight when i try to play with grub config. (in previous). And I remember some while reading this post [http://ubuntuforums.org/showpost.php?p=733325&postcount=16](http://ubuntuforums.org/showpost.php?p=733325&postcount=16)
This newbie has a similiar problems...

grub does not recognized my ntfs partition while booting.[-( 

[FONT="Courier New"]grub/menu.lst[/FONT]

```
=== 
title windows 
rootnoverify (hd2,0) 
chainloader +1 
=== 

```


here is my [FONT="Courier New"][SIZE="2"]fdisk -l[/SIZE][/FONT]  (as i remember):rolleyes: 

```
device         boot system   OS
dev/hda1      *      NTFS     XP
dev/hda4              NTFS
dev/hda5              NTFS

dev/hdb1      *      FAT32   none

dev/hda1      *      ext3      ubuntu
dev/hda5              swap
```
Could anyone give me a link?[/QUOTE]

Did you add those 'map' commands to menu.lst? Try also with
```
rootnoverify (hd1)
``` instead of ```
rootnoverify (hd1,0)
```

---

### Post by Pavel Kraynov on 2006-02-16
ok. it's work
thanks all very much.

---

