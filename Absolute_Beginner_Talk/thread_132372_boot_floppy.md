---
title: "boot floppy?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-02-18
I installed Ubuntu on partition 3.

I have Windows 2000 on partition 1.

and Windows 98 on partition 2.

I have a third party boot manager that works on 1 and 2.

Therefore I did not install GRUB because I don't want to mess that up.

Partition 3 will not boot because there is no GRUB (I guess).

How can I make a floppy to boot from? As I read you can do.

Don Cole

---

### Post by Ghetto_Smurf on 2006-02-18
never had a dual OS system without a boot manager, but case you have an slackware install disc (the second one), it will search for linux systems and boot them. 

case you havent got a slack disk, you have rawrite for windows, to create a boot floppy

---

### Post by don cole on 2006-02-18
I have a Boot Manager it's in the MBR writen by Ranish Partition Manager.
\
Don Cole

---

### Post by Bartender on 2006-02-18
Hi, Don -
Did you take a look at the .pdf on the Ranish website describing a Linux dual-boot?
[http://www.ranish.com/part/dualboot.pdf](http://www.ranish.com/part/dualboot.pdf)
Don't know if this is any help
It seems like a well-crafted guide.  It refers to a Linux partitioner that isn't GRUB but probly works the same(?)
At the end he mentions that RPM can't handle more than 4 primary partitions.  How many primary's do you have now?

---

### Post by cotcot on 2006-02-18
During install of ubuntu answer "no" on the question whether to install grub bootloader in MBR. You then get the question where to install it. Answer "/dev/fd0". Set your hda1 (the partition where you have your third party bootloader) active again with fdisk. (Ubuntu has set your hda3 active during install)

If you have ubuntu already installed : put in a live CD and mount hda3, go to /boot/grub and do "grub-install /dev/fd0". In but grub you have the stage 1, 1.5 and 2 as well as menu.lst.

---

### Post by Bartender on 2006-02-18
cotcot -
A little clarification please.  If a guy were able to follow your directions, would he have to use the floppy each time to access the Ubuntu partition?
Thanks

---

