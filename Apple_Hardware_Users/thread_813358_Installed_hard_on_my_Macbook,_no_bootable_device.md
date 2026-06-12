---
title: "Installed hard on my Macbook, no bootable device?"
date: 2008-05-30
forum: Apple Hardware Users
---

### Post by AmbroseBSOD on 2008-05-30
I've recently installed Hardy Heron (x86) on my macbook 4.1.
Partition as follows

/boot 200MB sda4
/ 24000MB sda5
Swap 2000MB

In the advanced option i choose to install the grub to sda4.

Installation goes fine but when I reboot and choose Ubuntu from the boot loader (rEFIt) i get eh message that there is no bootable device and to insert a bootable disk and reboot.

Can anyone provide suggestions as to why this isn't working?
I followed this exact procedure with fedora 9 without issue, and I'm a little confused.


Thanks in advanced!

AmbroseBSOD

---

### Post by cyberdork33 on 2008-05-30
There is a Bug in the installer.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by AmbroseBSOD on 2008-05-30
Thanks alot!

---

### Post by AmbroseBSOD on 2008-05-30
Followed instructions, but when I try to redo grub I've hit a snag.

Entered:
sudo grub
find /boot/grub/stage1

I get:

error 15 file not found

How do I get around this/correct it?

---

### Post by cyberdork33 on 2008-05-31
> **AmbroseBSOD said:**
> Followed instructions, but when I try to redo grub I've hit a snag.

Entered:
sudo grub
find /boot/grub/stage1

I get:

error 15 file not found

How do I get around this/correct it?
because you have a separate boot partition, grub with not be inside a folder named /boot. try 'find /grub/stage1'

---

### Post by AmbroseBSOD on 2008-05-31
Thanks, works much better that way :)

---

