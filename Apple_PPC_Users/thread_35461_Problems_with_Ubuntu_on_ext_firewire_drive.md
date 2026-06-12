---
title: "Problems with Ubuntu on ext firewire drive"
date: 2005-05-19
forum: Apple PPC Users
---

### Post by birdseed on 2005-05-19
OK,
So I want to move into the world of Linux, but decided to do so from the comfort of an external hard drive. I have a PB Ti SD with the old 60Gb HDD in a 2.5 enclosure, connected via Firewire. After trying many times to get Ubuntu to partition the disk, it did so, but now, even when using ExtFS Manager to mount it onto my Mac OS X desktop, I cannot reformat the disk back to Mac. This is a bit of a worry, as I was merely trying it all as an experiment and I do not want to kill my hard drive for good. Disk Utility on the Mac crashes each time I try to use it now, b/c of the ext disk. Any ideas as to how to overcome this issue?
Thanks!

---

### Post by Len on 2005-05-19
That crash is strange... You could try removing all partitions with the Ubuntu Install CD and try to format it with the mac again.

You cannot damage the disk in any way with Ubuntu (no software can do this actually), so if it is broken it probably was going down if you didn't install Ubuntu as well. It also can be a bad firewire cable.

But I do not expect that. Just empty the disk with Ubuntu or Mac OS 9, you can try even DOS or Windows and then go back to OS X and try to format it again.
First, if you haven't tried already, select the whole device in Disk Utility, not a separate partition and format away.

You can also do it the unix way within OS X: write some zeroes to the disk to destroy the problem partition map, let ```
sudo dd if=/dev/null of=/dev/<yourunixdiskname> bs=1048576 count=512
``` run in a terminal to write 512 MB of zeroes to it. I never tried it on harddisks but I suppose it works and starts at the first sector just like on other devices and hopefully will destroy the partition map. Be sure to fill in the disk address and not the partition address. 512 MB is overkill, but to be sure :), just don't pick the wrong disk!
You can get the unix name of your disk by opening disk utility and getting info on the firewire disk, something like 'disk4'.

---

### Post by birdseed on 2005-05-19
Hmmm....

Disk Utility was unable to do anything, as it crashed every time the external disk was connected to the external hard disk. ](*,) However, I have now managed to get my disk back to life, by going into the Ubuntu installer and fiddling with the partitioning part and then exiting, and going back to the Mac.

I am unsure as to what the disk should be partitioned to in Ubuntu. The guided partitioning never seems to work, jamming half way through the write process. If I divide the main part of the drive and make a /home partition, it (mostly) executes the write process. Is this a good idea?

The process seems to fail when I get to the part of installing yaboot. It jams every time. Where is this app stored if I am installing it on an ext HDD? What is the keystroke to choose one OS or the other? Is this different when using an ext HDD?

I would really like to get this going, any help is greatly appreciated.

Thanks!

---

### Post by Len on 2005-05-20
Strange...

I'm not too familiar with Yaboot. I think it is installed at your external firewire drive. It is strange that the partitioning fails; I'd try the autopartition option to let Ubuntu automatically fill in the partitions on the free space of the drive for you to see if that works. 
If it doesn't, you just found a bug or your drive isn't good.
You also could try to zero the device with Disk Utility. Make one free space 'partition' (or two, one HFS+ if you want a MacOS partition as well) and try again.

And again, don't worry; you cannot destroy your drive. If it breaks it was doomed to break anyway.

General note: I didn't see a 'bootstrap' partition mentioned for a long while in those new linux versions. In the past you made one to install Yaboot on and selected that 10 MB partition as the bootable partition, type "bootstrap".



[color=red]--- A bit off topic but maybe useful for Yaboot ---[/color]
If all goes well but the mac won't boot Linux just hold the 'alt' key when powering your Mac and it should appear there. If you're familiar with the OpenFirmware you also might want to issue a boot command on the Yaboot partition if it is not listed, but all of this is only useful if the Ubuntu installation actually finishes...

Another reason for the failiure of the install of Yaboot might be corrupt NVRAM. Hold Apple+Alt+P+R when booting your mac to get into the openfirmware and type:
reset-nvram
set-defaults
reset-all
to reset your openfirmware. A bit overkill but it might work as a last solution. This will reset the date and time and startup disk, nothing else.
[color=red]--- end off topic ---[/color]

Good luck! If all fails try to install Mac OS X on the external drive to see if that works to verify the drive is really bootable and works.

---

