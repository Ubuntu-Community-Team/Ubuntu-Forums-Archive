---
title: "Grub2 Boot CD for Intel Macs."
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by pxwpxw on 2009-02-02
Found on the Wubi forum sticky (May 2007).

**Bootable cdrom image of grub2**

It is grub2-pcbios, not efi. 
Works on MacBook2,1 and Imac8,1 and hopefully all intelmacs as linux rescue cd.
Uses the new exetnsive grub2 commands. Very useful to get back into ubuntu or just check out partitions if grub1 fails.

You will have to use the grub> command line
Choose your own linux root=
 vga=773 is 1024x768

```

grub> search --set /vmlunuz
grub> linux /vmlinuz root=/dev/sda3 vga=773
grub> initrd /initrd.img
grub> boot

```

Can also do chainloader to grub1 or windows
Not mac osx.
Probably does not need MBR to boot linux (uses gpt). 
Can not see external drive.

Sticky:    Use grub2 to test filesystem issue
**bean123** (bean is a grub dev)
[http://ubuntuforums.org/showthread.php?t=877750](http://ubuntuforums.org/showthread.php?t=877750)
**Bootable cdrom image of grub2**

The link on post #1  broken - go to update on post #6.

get the latest currently  grub2-2009-01-13.iso.bz2 3.4MB
unzip and burn iso to cd at low speed using Mac OSX Disk Utility.

---

