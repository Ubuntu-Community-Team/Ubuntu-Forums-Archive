---
title: "Recommended partitions for older system"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by _Mike_ on 2006-10-09
I need some recommendations on manually setting up partitions when installing from the alternate (text mode) CD. On my 1st installation attempt, I chose to let it create the partitions automaticly but it wouldn't boot from the HD due to a GRUB Loading Error 18 which seemed to be caused by the BIOS not being able to boot from a portion of the HD above the 1023 sector. I've since tried to manually create the partitions but have ran into problems loading software from the CD.

What partitions do I need to create ( type, size, etc.) ? How do I make sure the boot partition is in a position to be readable by the BIOS?

---

### Post by Sef on 2006-10-09
This is error message 18:

> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Have you installed a new hard disk on your computer?  You could look into updating your BIOS, but you do have to be careful because you can mess up your system.  Maybe someone else has a better answer.

---

### Post by kidders on 2006-10-09
Hi there,

My understanding is that you should be fine if you create a small /boot partition and put it at the start of your disk. If another OS is using the first slot, you might run into difficulty though ... if it's not Linux, you won't necessarily be able to just move it around.

Boot partitions can be quite small. 32MB should be at least twice as much space as you'd need under "normal" circumstances.

Sef's suggestion may solve your problem more permanently though ... particularly if you have a dual BIOS, you should keep it up to date :-)

**Edit:** Hmm... Me or a staff member?! I'd go with the latter :P

---

### Post by _Mike_ on 2006-10-09
The BIOS has the latest update available installed. 

Both hard drives are clean, no OS installed.

What I'm looking for is a partition "set up" similar to this:

/boot  xxMB  ext3(filesystem) logical/extended   bootable?
/swap  xxMB  swap......................................
/(root)......................
/usr...................................

Do I need any partitions other than boot, swap, and root?

How do I make sure that the boot partition is positioned on the drive to be read by the BIOS?

---

### Post by kidders on 2006-10-09
Hey again,

As I said in my last post, if you make /boot small (and first!), you should be fine afaik. Having said that, I've never encountered this particular problem myself.

> Do I need any partitions other than boot, swap, and root?
That leaves you with 3 filesystems, but you can use more if you'd like to. It's not something I'd recommend, unless you can come up with a specific benefit that outweighs the disadvantages of doing so. Many people (including me) like to keep /home separate, for recovery purposes, or for use with multiple OSs.

---

