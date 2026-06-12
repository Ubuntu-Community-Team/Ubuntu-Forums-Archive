---
title: "grun error    urgent help"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-08
my dad installed ubuntu as a dual boot on his xp laptop. but its coming up as grub errror 17 wheb he boots up. he cant get into any OS

please help

BTW: he can get into the bios

---

### Post by Pragmatist on 2006-03-08
According to the GRUB manual: 
> [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)
a number 17 error is > Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

You need to boot the computer from a medium other than your hard drive, since the hard drive is not bootable right now.  One approach is to use a boot disk (on a floppy or a CD).  Another approach is to use a LiveCD such as Knoppix.

If you already made an ubuntu boot disk, then use that.  You set your boot order in the BIOS and make sure floppy is first.  When you get to the prompt type rescue (or hit the function key for more options and use the option that has the word rescue in it).  This will boot a small linux system that runs from your floppy.  From there you can use some basic tools to troubleshoot your hard drive.  What we need is to see your partition table.  To do that you run the fdisk command:
```
fdisk /dev/hda
```
You'll get a prompt like this: > Command (m for help): type ```
p
``` to print the partition table.  Write it down exactly as it is, and give it to us here.

You can also use Knoppix which is a LiveCD distribution.  LiveCD is a similar idea to the boot disk in that it runs Linux off of the CD.  However a LiveCD like Knoppix is a full-fledged system and will give you much more tools to use (for one thing because a CD can hold much more than a floppy.)  Get yourself a copy at [http://linuxiso.org](http://linuxiso.org)  You can use this to do the same thing (fdisk /dev/hda)  
**Note this assumes that your hard drive is at /dev/hda**

---

